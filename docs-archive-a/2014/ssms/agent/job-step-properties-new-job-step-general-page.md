---
title: '작업 단계 속성: 새 작업 단계 (일반 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: stevestein
ms.author: sstein
ms.openlocfilehash: c76e1ecb69a1475ec102f143a6a1ca34fbf91e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653106"
---
# <a name="job-step-properties-new-job-step-general-page"></a><span data-ttu-id="703c7-102">작업 단계 속성: 새 작업 단계(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="703c7-102">Job Step Properties: New Job Step (General Page)</span></span>
  <span data-ttu-id="703c7-103">이 페이지를 사용 하 여 에이전트 작업 단계의 속성을 확인 하 고 변경 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하거나 새 작업 단계를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step, or to define a new job step.</span></span>  
  
 <span data-ttu-id="703c7-104">이 페이지로 이동하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 확장한 다음 **작업**을 마우스 오른쪽 단추로 클릭하고 **새 작업**을 클릭한 다음 **단계** 페이지를 선택하고 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-104">To navigate to this page, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, click **New Jobs**, select the **Steps** page, and click **New**.</span></span> <span data-ttu-id="703c7-105">개체 탐색기에서 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 **단계** 를 선택하고 **새로 만들기**, **삽입**또는 **편집**을 클릭하여 이 페이지로 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-105">You can also navigate to this page by right-clicking a job in Object Explorer, clicking **Properties**, selecting the **Steps** page, and clicking **New**, **Insert**, or **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="703c7-106">옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-106">Options</span></span>  
 <span data-ttu-id="703c7-107">**단계 이름**</span><span class="sxs-lookup"><span data-stu-id="703c7-107">**Step name**</span></span>  
 <span data-ttu-id="703c7-108">작업 단계의 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-108">Set the name of the job step.</span></span>  
  
 <span data-ttu-id="703c7-109">**형식**</span><span class="sxs-lookup"><span data-stu-id="703c7-109">**Type**</span></span>  
 <span data-ttu-id="703c7-110">작업 단계에서 사용하는 하위 시스템을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-110">Set the subsystem that the job step uses.</span></span> <span data-ttu-id="703c7-111">선택한 하위 시스템에 따라 작업 단계 정의에 표시되는 옵션이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-111">Based on the subsystem you choose, the options displayed for defining the job step change.</span></span>  
  
 <span data-ttu-id="703c7-112">**다음 계정으로 실행**</span><span class="sxs-lookup"><span data-stu-id="703c7-112">**Run as**</span></span>  
 <span data-ttu-id="703c7-113">작업 단계에 사용할 프록시 계정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-113">Set the proxy account for the job step.</span></span> <span data-ttu-id="703c7-114">sysadmin 고정 서버 역할의 멤버는 **SQL 에이전트 서비스 계정**도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-114">Members of the sysadmin fixed server role may also specify the **SQL Agent Service Account**.</span></span>  
  
 <span data-ttu-id="703c7-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="703c7-115">**Database**</span></span>  
 <span data-ttu-id="703c7-116">작업 단계가 실행되는 데이터베이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-116">Set the database that the job step runs in.</span></span> <span data-ttu-id="703c7-117">일부 작업 단계 유형에 대해서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-117">This option is not available for all job step types.</span></span>  
  
 <span data-ttu-id="703c7-118">**명령**</span><span class="sxs-lookup"><span data-stu-id="703c7-118">**Command**</span></span>  
 <span data-ttu-id="703c7-119">작업 단계에서 실행하는 명령을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-119">Set the command that the job step runs.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="703c7-120">Transact-SQL 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-120">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="703c7-121">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-121">**Open**</span></span>  
 <span data-ttu-id="703c7-122">파일에서 명령을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-122">Load the command from a file.</span></span>  
  
 <span data-ttu-id="703c7-123">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-123">**Select All**</span></span>  
 <span data-ttu-id="703c7-124">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-124">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-125">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-125">**Copy**</span></span>  
 <span data-ttu-id="703c7-126">선택한 텍스트를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-126">Copy the selected text to the Clipboard.</span></span>  
  
 <span data-ttu-id="703c7-127">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-127">**Paste**</span></span>  
 <span data-ttu-id="703c7-128">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-128">Paste the contents of the Clipboard.</span></span>  
  
 <span data-ttu-id="703c7-129">**Parse**</span><span class="sxs-lookup"><span data-stu-id="703c7-129">**Parse**</span></span>  
 <span data-ttu-id="703c7-130">명령의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-130">Check the syntax of the command.</span></span>  
  
## <a name="options-for-activex-script-job-steps"></a><span data-ttu-id="703c7-131">ActiveX 스크립트 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-131">Options for ActiveX Script Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="703c7-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 이후 버전에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트에서 ActiveX 스크립팅 하위 시스템이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-132">The ActiveX Scripting subsystem will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="703c7-133">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="703c7-133">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="703c7-134">**VBScript**</span><span class="sxs-lookup"><span data-stu-id="703c7-134">**VBScript**</span></span>  
 <span data-ttu-id="703c7-135">작업 단계에 사용할 언어로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-135">Specify [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition as the language for the job steps.</span></span>  
  
 <span data-ttu-id="703c7-136">**JScript**</span><span class="sxs-lookup"><span data-stu-id="703c7-136">**JScript**</span></span>  
 <span data-ttu-id="703c7-137">작업 단계에 사용할 언어로 JScript를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-137">Specify JScript as the language for the job steps.</span></span>  
  
 <span data-ttu-id="703c7-138">**기타**</span><span class="sxs-lookup"><span data-stu-id="703c7-138">**Other**</span></span>  
 <span data-ttu-id="703c7-139">다른 스크립트 언어로 작성된 작업 단계에 사용할 언어 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-139">Type the name of the language for job steps written in another scripting language.</span></span>  
  
 <span data-ttu-id="703c7-140">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-140">**Open**</span></span>  
 <span data-ttu-id="703c7-141">파일에서 명령을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-141">Load the command from a file.</span></span>  
  
 <span data-ttu-id="703c7-142">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-142">**Select All**</span></span>  
 <span data-ttu-id="703c7-143">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-143">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-144">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-144">**Copy**</span></span>  
 <span data-ttu-id="703c7-145">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-145">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-146">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-146">**Paste**</span></span>  
 <span data-ttu-id="703c7-147">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-147">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="703c7-148">운영 체제(CmdExec) 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-148">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="703c7-149">**성공한 명령의 프로세스 종료 코드**</span><span class="sxs-lookup"><span data-stu-id="703c7-149">**Process exit code of a successful command**</span></span>  
 <span data-ttu-id="703c7-150">성공을 나타내기 위해 명령에서 반환하는 종료 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-150">Type the exit code that the command returns to indicate success.</span></span>  
  
 <span data-ttu-id="703c7-151">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-151">**Open**</span></span>  
 <span data-ttu-id="703c7-152">파일에서 명령을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-152">Load the command from a file.</span></span>  
  
 <span data-ttu-id="703c7-153">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-153">**Select All**</span></span>  
 <span data-ttu-id="703c7-154">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-154">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-155">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-155">**Copy**</span></span>  
 <span data-ttu-id="703c7-156">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-156">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-157">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-157">**Paste**</span></span>  
 <span data-ttu-id="703c7-158">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-158">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="703c7-159">PowerShell 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-159">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="703c7-160">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-160">**Open**</span></span>  
 <span data-ttu-id="703c7-161">파일로부터 스크립트를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-161">Load the script from a file.</span></span>  
  
 <span data-ttu-id="703c7-162">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-162">**Select All**</span></span>  
 <span data-ttu-id="703c7-163">스크립트의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-163">Select the text of the script.</span></span>  
  
 <span data-ttu-id="703c7-164">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-164">**Copy**</span></span>  
 <span data-ttu-id="703c7-165">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-165">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-166">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-166">**Paste**</span></span>  
 <span data-ttu-id="703c7-167">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-167">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-distributor-job-steps"></a><span data-ttu-id="703c7-168">복제 배포자 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-168">Options for Replication Distributor Job Steps</span></span>  
 <span data-ttu-id="703c7-169">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-169">**Select All**</span></span>  
 <span data-ttu-id="703c7-170">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-170">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-171">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-171">**Copy**</span></span>  
 <span data-ttu-id="703c7-172">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-172">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-173">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-173">**Paste**</span></span>  
 <span data-ttu-id="703c7-174">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-174">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-merge-job-steps"></a><span data-ttu-id="703c7-175">복제 병합 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-175">Options for Replication Merge Job Steps</span></span>  
 <span data-ttu-id="703c7-176">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-176">**Select All**</span></span>  
 <span data-ttu-id="703c7-177">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-177">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-178">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-178">**Copy**</span></span>  
 <span data-ttu-id="703c7-179">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-179">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-180">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-180">**Paste**</span></span>  
 <span data-ttu-id="703c7-181">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-181">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="703c7-182">복제 큐 판독기 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-182">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="703c7-183">**Database**</span><span class="sxs-lookup"><span data-stu-id="703c7-183">**Database**</span></span>  
 <span data-ttu-id="703c7-184">작업 단계에 사용할 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-184">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="703c7-185">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-185">**Select All**</span></span>  
 <span data-ttu-id="703c7-186">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-186">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-187">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-187">**Copy**</span></span>  
 <span data-ttu-id="703c7-188">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-188">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-189">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-189">**Paste**</span></span>  
 <span data-ttu-id="703c7-190">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-190">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-snapshot-job-steps"></a><span data-ttu-id="703c7-191">복제 스냅샷 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-191">Options for Replication Snapshot Job Steps</span></span>  
 <span data-ttu-id="703c7-192">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-192">**Select All**</span></span>  
 <span data-ttu-id="703c7-193">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-193">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-194">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-194">**Copy**</span></span>  
 <span data-ttu-id="703c7-195">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-195">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-196">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-196">**Paste**</span></span>  
 <span data-ttu-id="703c7-197">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-197">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a><span data-ttu-id="703c7-198">복제 트랜잭션 로그 판독기 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-198">Options for Replication Transaction-Log Reader Job Steps</span></span>  
 <span data-ttu-id="703c7-199">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-199">**Select All**</span></span>  
 <span data-ttu-id="703c7-200">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-200">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-201">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-201">**Copy**</span></span>  
 <span data-ttu-id="703c7-202">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-202">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-203">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-203">**Paste**</span></span>  
 <span data-ttu-id="703c7-204">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-204">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a><span data-ttu-id="703c7-205">SQL Server Analysis Services 명령 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-205">Options for SQL Server Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="703c7-206">**Server**</span><span class="sxs-lookup"><span data-stu-id="703c7-206">**Server**</span></span>  
 <span data-ttu-id="703c7-207">작업 단계를 실행할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-207">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="703c7-208">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-208">**Open**</span></span>  
 <span data-ttu-id="703c7-209">파일에서 명령을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-209">Load the command from a file.</span></span>  
  
 <span data-ttu-id="703c7-210">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-210">**Select All**</span></span>  
 <span data-ttu-id="703c7-211">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-211">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-212">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-212">**Copy**</span></span>  
 <span data-ttu-id="703c7-213">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-213">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-214">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-214">**Paste**</span></span>  
 <span data-ttu-id="703c7-215">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-215">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a><span data-ttu-id="703c7-216">SQL Server Analysis Services 쿼리 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-216">Options for SQL Server Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="703c7-217">**Server**</span><span class="sxs-lookup"><span data-stu-id="703c7-217">**Server**</span></span>  
 <span data-ttu-id="703c7-218">작업 단계를 실행할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-218">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="703c7-219">**Database**</span><span class="sxs-lookup"><span data-stu-id="703c7-219">**Database**</span></span>  
 <span data-ttu-id="703c7-220">작업 단계에 사용할 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-220">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="703c7-221">**열기**</span><span class="sxs-lookup"><span data-stu-id="703c7-221">**Open**</span></span>  
 <span data-ttu-id="703c7-222">파일에서 명령을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-222">Load the command from a file.</span></span>  
  
 <span data-ttu-id="703c7-223">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="703c7-223">**Select All**</span></span>  
 <span data-ttu-id="703c7-224">명령의 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-224">Select the text of the command.</span></span>  
  
 <span data-ttu-id="703c7-225">**복사**</span><span class="sxs-lookup"><span data-stu-id="703c7-225">**Copy**</span></span>  
 <span data-ttu-id="703c7-226">선택한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-226">Copy the selected text.</span></span>  
  
 <span data-ttu-id="703c7-227">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="703c7-227">**Paste**</span></span>  
 <span data-ttu-id="703c7-228">클립보드의 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-228">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a><span data-ttu-id="703c7-229">Integration Services 패키지 실행 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="703c7-229">Options for Integration Services Package Execution Job Steps</span></span>  
  
### <a name="general-tab"></a><span data-ttu-id="703c7-230">일반 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-230">General Tab</span></span>  
 <span data-ttu-id="703c7-231">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 패키지가 있는 위치와 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-231">Specify where the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package is located and what authentication method to use.</span></span> <span data-ttu-id="703c7-232">이 탭을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-232">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="703c7-233">**패키지 원본**</span><span class="sxs-lookup"><span data-stu-id="703c7-233">**Package source**</span></span>  
 <span data-ttu-id="703c7-234">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지가 저장된 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-234">Specify where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="703c7-235">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-235">Choose one of the following:</span></span>  
  
-   <span data-ttu-id="703c7-236">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="703c7-236">**SQL Server**</span></span>  
  
-   <span data-ttu-id="703c7-237">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="703c7-237">**File system**</span></span>  
  
-   <span data-ttu-id="703c7-238">**SSIS 패키지 저장소**</span><span class="sxs-lookup"><span data-stu-id="703c7-238">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="703c7-239">**Server**</span><span class="sxs-lookup"><span data-stu-id="703c7-239">**Server**</span></span>  
 <span data-ttu-id="703c7-240">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지가 저장된 서버 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-240">Type the server name where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="703c7-241">이 옵션은 **패키지 원본** 에 대해 **SQL Server** 또는 **SSIS 패키지 저장소**를 지정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-241">This option is only available when **SQL Server** or **SSIS Package Store** is specified for **Package Source**.</span></span>  
  
 <span data-ttu-id="703c7-242">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="703c7-242">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="703c7-243">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 시 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-243">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="703c7-244">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="703c7-244">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="703c7-245">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-245">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="703c7-246">이 인증 방법을 선택하는 경우 해당 **사용자 이름** 과 **암호**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-246">If this method of authentication is selected, enter the appropriate **User name** and **Password**.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="703c7-247">인증은 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-247">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="703c7-248">보안 향상을 위해 가능하면 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-248">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="703c7-249">**패키지**</span><span class="sxs-lookup"><span data-stu-id="703c7-249">**Package**</span></span>  
 <span data-ttu-id="703c7-250">패키지 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-250">Type the location of the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="703c7-251">암호로 보호된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 경우 **구성** 탭을 클릭하여 **패키지 암호** 대화 상자에 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-251">For password-protected [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages, click the **Configurations** tab to enter the password in the **Package Password** dialog box.</span></span> <span data-ttu-id="703c7-252">그렇지 않으면 암호로 보호된 패키지를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-252">Otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that executes the password-protected package will fail.</span></span>  
  
### <a name="configurations-tab"></a><span data-ttu-id="703c7-253">구성 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-253">Configurations Tab</span></span>  
 <span data-ttu-id="703c7-254">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 구성 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-254">Specify configuration options for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="703c7-255">이 탭을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-255">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="703c7-256">**구성 파일**</span><span class="sxs-lookup"><span data-stu-id="703c7-256">**Configuration files**</span></span>  
 <span data-ttu-id="703c7-257">패키지의 구성 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-257">Lists the configuration files for the package.</span></span>  
  
 <span data-ttu-id="703c7-258">**추가**</span><span class="sxs-lookup"><span data-stu-id="703c7-258">**Add**</span></span>  
 <span data-ttu-id="703c7-259">패키지의 구성 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-259">Add a configuration file for the package.</span></span>  
  
 <span data-ttu-id="703c7-260">**제거**</span><span class="sxs-lookup"><span data-stu-id="703c7-260">**Remove**</span></span>  
 <span data-ttu-id="703c7-261">패키지의 구성 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-261">Remove a configuration file for the package.</span></span>  
  
 <span data-ttu-id="703c7-262">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="703c7-262">**Move Up**</span></span>  
 <span data-ttu-id="703c7-263">선택한 구성 파일을 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-263">Move the selected configuration file up.</span></span>  
  
 <span data-ttu-id="703c7-264">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="703c7-264">**Move Down**</span></span>  
 <span data-ttu-id="703c7-265">선택한 구성 파일을 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-265">Move the selected configuration file down.</span></span>  
  
### <a name="command-files-tab"></a><span data-ttu-id="703c7-266">명령 파일 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-266">Command Files Tab</span></span>  
 <span data-ttu-id="703c7-267">패키지의 명령 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-267">Select command files for the package.</span></span> <span data-ttu-id="703c7-268">명령 파일은 목록에 나타나는 순서대로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-268">Command files are processed in the order in which they appear in the list.</span></span> <span data-ttu-id="703c7-269">이 탭을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-269">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="703c7-270">**명령 파일**</span><span class="sxs-lookup"><span data-stu-id="703c7-270">**Command files**</span></span>  
 <span data-ttu-id="703c7-271">패키지의 명령 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-271">Lists the command files for the package.</span></span>  
  
 <span data-ttu-id="703c7-272">**추가**</span><span class="sxs-lookup"><span data-stu-id="703c7-272">**Add**</span></span>  
 <span data-ttu-id="703c7-273">명령 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-273">Add a command file.</span></span>  
  
 <span data-ttu-id="703c7-274">**제거**</span><span class="sxs-lookup"><span data-stu-id="703c7-274">**Remove**</span></span>  
 <span data-ttu-id="703c7-275">선택한 명령 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-275">Remove the selected command file.</span></span>  
  
 <span data-ttu-id="703c7-276">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="703c7-276">**Move Up**</span></span>  
 <span data-ttu-id="703c7-277">선택한 명령 파일을 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-277">Move the selected command file up.</span></span>  
  
 <span data-ttu-id="703c7-278">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="703c7-278">**Move Down**</span></span>  
 <span data-ttu-id="703c7-279">선택한 명령 파일을 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-279">Move the selected command file down.</span></span>  
  
### <a name="data-sources-tab"></a><span data-ttu-id="703c7-280">데이터 원본 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-280">Data Sources Tab</span></span>  
 <span data-ttu-id="703c7-281">패키지에 지정된 데이터 원본이 이 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-281">View the data sources specified in the package on this tab.</span></span>  
  
 <span data-ttu-id="703c7-282">**연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="703c7-282">**Connection Manager**</span></span>  
 <span data-ttu-id="703c7-283">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-283">View the name of the data source.</span></span>  
  
 <span data-ttu-id="703c7-284">**설명**</span><span class="sxs-lookup"><span data-stu-id="703c7-284">**Description**</span></span>  
 <span data-ttu-id="703c7-285">데이터 원본에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-285">View the description of the data source.</span></span>  
  
 <span data-ttu-id="703c7-286">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="703c7-286">**Connection String**</span></span>  
 <span data-ttu-id="703c7-287">데이터 원본에 대한 연결 문자열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-287">View the connection string for the data source.</span></span>  
  
### <a name="execution-options-tab"></a><span data-ttu-id="703c7-288">실행 옵션 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-288">Execution Options Tab</span></span>  
 <span data-ttu-id="703c7-289">이 탭에서 패키지의 실행 옵션을 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-289">View or change the execution options for the package on this tab.</span></span>  
  
 <span data-ttu-id="703c7-290">**유효성 검사 경고 발생 시 패키지 실패**</span><span class="sxs-lookup"><span data-stu-id="703c7-290">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="703c7-291">유효성 검사 경고가 발생하는 경우 패키지 실행이 실패하도록 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-291">Select this option for package execution to fail if validation warnings occur.</span></span>  
  
 <span data-ttu-id="703c7-292">**패키지를 실행하지 않고 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="703c7-292">**Validate package without executing**</span></span>  
 <span data-ttu-id="703c7-293">작업 단계에서 패키지를 실행하지 않고 유효성을 검사하도록 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-293">Select this option for the job step to validate, but not execute, the package.</span></span>  
  
 <span data-ttu-id="703c7-294">**최대 동시 실행 파일 수**</span><span class="sxs-lookup"><span data-stu-id="703c7-294">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="703c7-295">한 번에 실행할 수 있는 최대 실행 파일 수입니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-295">Maximum number of executable files that can run at one time.</span></span>  
  
 <span data-ttu-id="703c7-296">**패키지 검사점 사용**</span><span class="sxs-lookup"><span data-stu-id="703c7-296">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="703c7-297">작업 단계에서 패키지 검사점을 사용하도록 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-297">Select this option for the job step to use package checkpoints.</span></span>  
  
 <span data-ttu-id="703c7-298">**검사점 파일**</span><span class="sxs-lookup"><span data-stu-id="703c7-298">**Checkpoint file**</span></span>  
 <span data-ttu-id="703c7-299">패키지 검사점 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-299">Type the name of the package checkpoint file.</span></span>  
  
 <span data-ttu-id="703c7-300">**...**</span><span class="sxs-lookup"><span data-stu-id="703c7-300">**...**</span></span>  
 <span data-ttu-id="703c7-301">패키지 검사점 파일을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-301">Browse to find the package checkpoint file.</span></span>  
  
 <span data-ttu-id="703c7-302">**다시 시작 옵션 무시**</span><span class="sxs-lookup"><span data-stu-id="703c7-302">**Override restart options**</span></span>  
 <span data-ttu-id="703c7-303">이 작업 단계에 대해 패키지에 지정된 것과 다른 다시 시작 옵션을 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-303">Select this option to specify restart options for this job step that are different from the restart options specified in the package.</span></span>  
  
 <span data-ttu-id="703c7-304">**다시 시작 옵션**</span><span class="sxs-lookup"><span data-stu-id="703c7-304">**Restart option**</span></span>  
 <span data-ttu-id="703c7-305">패키지가 다시 시작될 때 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-305">Select the action to take when the package restarts.</span></span>  
  
### <a name="logging-tab"></a><span data-ttu-id="703c7-306">로깅 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-306">Logging Tab</span></span>  
 <span data-ttu-id="703c7-307">이 탭에서 패키지의 로그 공급자를 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-307">View or change the log providers for the package on this tab.</span></span>  
  
 <span data-ttu-id="703c7-308">**로그 공급자**</span><span class="sxs-lookup"><span data-stu-id="703c7-308">**Log Provider**</span></span>  
 <span data-ttu-id="703c7-309">로그 공급자의 ClassID를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-309">Select the ClassID for the log provider.</span></span>  
  
 <span data-ttu-id="703c7-310">**구성 문자열**</span><span class="sxs-lookup"><span data-stu-id="703c7-310">**Configuration String**</span></span>  
 <span data-ttu-id="703c7-311">로그 공급자의 구성 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-311">Type the configuration string for the log provider.</span></span>  
  
 <span data-ttu-id="703c7-312">**제거**</span><span class="sxs-lookup"><span data-stu-id="703c7-312">**Remove**</span></span>  
 <span data-ttu-id="703c7-313">로그 공급자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-313">Removes the log provider.</span></span>  
  
### <a name="set-values-tab"></a><span data-ttu-id="703c7-314">값 설정 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-314">Set Values Tab</span></span>  
 <span data-ttu-id="703c7-315">이 탭에서 패키지의 속성 값을 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-315">View or change property values for the package on this tab.</span></span>  
  
 <span data-ttu-id="703c7-316">**속성 경로**</span><span class="sxs-lookup"><span data-stu-id="703c7-316">**Property path**</span></span>  
 <span data-ttu-id="703c7-317">속성 경로를 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-317">View or change the path for the property.</span></span>  
  
 <span data-ttu-id="703c7-318">**값**</span><span class="sxs-lookup"><span data-stu-id="703c7-318">**Value**</span></span>  
 <span data-ttu-id="703c7-319">속성 값을 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-319">View or change the value for the property.</span></span>  
  
 <span data-ttu-id="703c7-320">**제거**</span><span class="sxs-lookup"><span data-stu-id="703c7-320">**Remove**</span></span>  
 <span data-ttu-id="703c7-321">속성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-321">Removes the property.</span></span>  
  
### <a name="verification-tab"></a><span data-ttu-id="703c7-322">확인 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-322">Verification Tab</span></span>  
 <span data-ttu-id="703c7-323">이 탭에서 작업 단계의 확인 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-323">Select the verification options for the job step on this tab.</span></span>  
  
 <span data-ttu-id="703c7-324">**서명된 패키지만 실행**</span><span class="sxs-lookup"><span data-stu-id="703c7-324">**Execute only signed packages**</span></span>  
 <span data-ttu-id="703c7-325">서명된 패키지만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-325">Run only packages that have been signed.</span></span> <span data-ttu-id="703c7-326">이 옵션을 선택하면 패키지가 서명되지 않은 경우 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-326">When this option is selected, the job step fails if the package is unsigned.</span></span>  
  
 <span data-ttu-id="703c7-327">**패키지 빌드 확인**</span><span class="sxs-lookup"><span data-stu-id="703c7-327">**Verify package build**</span></span>  
 <span data-ttu-id="703c7-328">특정 빌드 번호가 있는 패키지만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-328">Run only packages with a specific build number.</span></span> <span data-ttu-id="703c7-329">이 옵션을 선택하면 지정한 빌드 번호가 패키지에 없는 경우 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-329">When this option is selected, the job step fails if the package does not have the specified build number.</span></span>  
  
 <span data-ttu-id="703c7-330">**빌드**</span><span class="sxs-lookup"><span data-stu-id="703c7-330">**Build**</span></span>  
 <span data-ttu-id="703c7-331">패키지의 빌드 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-331">Type the build number of the package.</span></span>  
  
 <span data-ttu-id="703c7-332">**패키지 ID 확인**</span><span class="sxs-lookup"><span data-stu-id="703c7-332">**Verify package ID**</span></span>  
 <span data-ttu-id="703c7-333">특정 ID가 있는 패키지만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-333">Run only packages with a specific ID.</span></span> <span data-ttu-id="703c7-334">이 옵션을 선택하면 지정한 ID가 패키지에 없는 경우 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-334">When this option is selected, the job step fails if the package does not have the specified ID.</span></span>  
  
 <span data-ttu-id="703c7-335">**패키지 ID**</span><span class="sxs-lookup"><span data-stu-id="703c7-335">**Package ID**</span></span>  
 <span data-ttu-id="703c7-336">패키지 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-336">Type the package ID.</span></span>  
  
 <span data-ttu-id="703c7-337">**버전 ID 확인**</span><span class="sxs-lookup"><span data-stu-id="703c7-337">**Verify version ID**</span></span>  
 <span data-ttu-id="703c7-338">특정 버전 ID가 있는 패키지만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-338">Run only packages with a specific version ID.</span></span> <span data-ttu-id="703c7-339">이 옵션을 선택하면 지정한 버전 ID가 패키지에 없는 경우 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-339">When this option is selected, the job step fails if the package does not have the specified version ID.</span></span>  
  
 <span data-ttu-id="703c7-340">**버전 ID**</span><span class="sxs-lookup"><span data-stu-id="703c7-340">**Version ID**</span></span>  
 <span data-ttu-id="703c7-341">버전 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-341">Type the version ID.</span></span>  
  
### <a name="command-line-tab"></a><span data-ttu-id="703c7-342">명령줄 탭</span><span class="sxs-lookup"><span data-stu-id="703c7-342">Command Line Tab</span></span>  
 <span data-ttu-id="703c7-343">패키지의 명령줄 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-343">Specify command-line options for the package.</span></span> <span data-ttu-id="703c7-344">이 탭을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-344">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="703c7-345">**원래 옵션 복원**</span><span class="sxs-lookup"><span data-stu-id="703c7-345">**Restore the original options**</span></span>  
 <span data-ttu-id="703c7-346">이 대화 상자에 설정된 명령줄 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-346">Use the command-line options set in this dialog.</span></span>  
  
 <span data-ttu-id="703c7-347">**수동으로 명령줄 편집**</span><span class="sxs-lookup"><span data-stu-id="703c7-347">**Edit the command line manually**</span></span>  
 <span data-ttu-id="703c7-348">명령줄 창에서 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-348">Specify options in the command-line window.</span></span>  
  
 <span data-ttu-id="703c7-349">**명령줄**</span><span class="sxs-lookup"><span data-stu-id="703c7-349">**Command line**</span></span>  
 <span data-ttu-id="703c7-350">이 패키지에 사용할 명령줄 옵션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="703c7-350">Type the command line options to use for this package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703c7-351">참고 항목</span><span class="sxs-lookup"><span data-stu-id="703c7-351">See Also</span></span>  
 <span data-ttu-id="703c7-352">[작업 단계 관리](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="703c7-352">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="703c7-353">[패키지에 대 한 SQL Server 에이전트 작업](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span><span class="sxs-lookup"><span data-stu-id="703c7-353">[SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span></span>  
 [<span data-ttu-id="703c7-354">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="703c7-354">Replication Agent Administration</span></span>](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
