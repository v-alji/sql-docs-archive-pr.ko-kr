---
title: SQL Server 에이전트에서 Windows PowerShell 작업 단계 실행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8c100e2eaf1f9b706087bd991fbc268540c29a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650141"
---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a><span data-ttu-id="81184-102">SQL Server 에이전트에서 Windows PowerShell 작업 단계 실행</span><span class="sxs-lookup"><span data-stu-id="81184-102">Run Windows PowerShell Steps in SQL Server Agent</span></span>
  <span data-ttu-id="81184-103">SQL Server 에이전트를 사용하여 일정에 따라 SQL Server PowerShell 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-103">Use SQL Server Agent to run SQL Server PowerShell scripts at schedule times.</span></span>  
  
1.  <span data-ttu-id="81184-104">**시작하기 전에:**  [제한 사항](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="81184-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="81184-105">**SQL Server 에이전트에서 PowerShell을 실행하려면:**  [PowerShell 작업 단계](#PShellJob), [명령 프롬프트 작업 단계](#CmdExecJob) 사용</span><span class="sxs-lookup"><span data-stu-id="81184-105">**To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="81184-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="81184-106">Before You Begin</span></span>  
 <span data-ttu-id="81184-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업 단계 유형은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-107">There are several types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="81184-108">각 유형은 복제 에이전트나 명령 프롬프트 환경과 같은 특정 환경을 구현하는 하위 시스템과 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-108">Each type is associated with a subsystem that implements a specific environment, such as a replication agent or command prompt environment.</span></span> <span data-ttu-id="81184-109">Windows PowerShell 스크립트를 코딩한 다음 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 사용하여 예약된 시간에 실행되거나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이벤트에 대한 응답으로 실행되는 스크립트를 작업에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-109">You can code Windows PowerShell scripts, and then use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to include the scripts in jobs that run at scheduled times or in response to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="81184-110">명령 프롬프트 작업 단계 또는 PowerShell 작업 단계를 사용하여 Windows PowerShell 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-110">Windows PowerShell scripts can be run using either a command prompt job step or a PowerShell job step.</span></span>  
  
1.  <span data-ttu-id="81184-111">PowerShell 작업 단계를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 하위 시스템에서 `sqlps` 유틸리티를 실행하도록 합니다. 이 유틸리티는 PowerShell 2.0을 시작하고 `sqlps` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81184-111">Use a PowerShell job step to have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent subsystem run the `sqlps` utility, which launches PowerShell 2.0 and imports the `sqlps` module.</span></span>  
  
2.  <span data-ttu-id="81184-112">명령 프롬프트 작업 단계를 사용하여 PowerShell.exe를 실행하고, `sqlps` 모듈을 가져오는 스크립트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-112">Use a command prompt job step to run PowerShell.exe, and specify a script that imports the `sqlps` module.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="81184-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="81184-113">Limitations and Restrictions</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="81184-114">PowerShell과 `sqlps` 모듈을 함께 실행하는 각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업 단계에서는 약 20MB의 메모리를 사용하는 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-114">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job step that runs PowerShell with the `sqlps` module launches a process which consumes approximately 20 MB of memory.</span></span> <span data-ttu-id="81184-115">따라서 많은 수의 Windows PowerShell 작업 단계를 동시에 실행하면 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-115">Running large numbers of concurrent Windows PowerShell job steps can adversely impact performance.</span></span>  
  
##  <a name="create-a-powershell-job-step"></a><a name="PShellJob"></a><span data-ttu-id="81184-116">PowerShell 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="81184-116">Create a PowerShell Job Step</span></span>  
 <span data-ttu-id="81184-117">**PowerShell 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="81184-117">**To create a PowerShell job step**</span></span>  
  
1.  <span data-ttu-id="81184-118">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="81184-119">작업을 만드는 방법은 [작업 만들기](../ssms/agent/create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81184-119">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="81184-120">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="81184-121">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="81184-122">**형식** 목록에서 **PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-122">In the **Type** list, click **PowerShell**.</span></span>  
  
5.  <span data-ttu-id="81184-123">**다음 계정으로 실행** 목록에서 작업에 사용할 자격 증명을 가진 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
6.  <span data-ttu-id="81184-124">**명령** 입력란에 작업 단계를 위해 실행될 PowerShell 스크립트 구문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-124">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="81184-125">아니면 **열기** 를 클릭한 다음 해당 스크립트 구문이 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-125">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
7.  <span data-ttu-id="81184-126">**고급** 페이지를 클릭하여 작업 단계가 성공 또는 실패할 경우에 수행할 동작, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트의 작업 단계 실행 시도 횟수, 그리고 다시 시도 간격 등 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="create-a-command-prompt-job-step"></a><a name="CmdExecJob"></a><span data-ttu-id="81184-127">명령 프롬프트 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="81184-127">Create a Command Prompt Job Step</span></span>  
 <span data-ttu-id="81184-128">**CmdExec 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="81184-128">**To create a CmdExec job step**</span></span>  
  
1.  <span data-ttu-id="81184-129">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-129">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="81184-130">작업을 만드는 방법은 [작업 만들기](../ssms/agent/create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81184-130">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="81184-131">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-131">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="81184-132">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-132">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="81184-133">**유형** 목록에서 **운영 체제(CmdExec)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-133">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
5.  <span data-ttu-id="81184-134">**다음 계정으로 실행** 목록에서 해당 작업이 사용할 자격 증명을 가진 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-134">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="81184-135">기본적으로 CmdExec 작업 단계는 SQL Server 에이전트 서비스 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="81184-135">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
6.  <span data-ttu-id="81184-136">**성공한 명령의 프로세스 종료 코드** 상자에 0에서 999999까지의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-136">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
7.  <span data-ttu-id="81184-137">**명령** 입력란에 실행할 PowerShell 스크립트를 지정하는 매개 변수와 함께 powershell.exe를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-137">In the **Command** box, enter powershell.exe with parameters specifying the PowerShell script to be run.</span></span>  
  
8.  <span data-ttu-id="81184-138">**고급** 페이지를 클릭하여 작업 단계의 성공 또는 실패 여부에 따라 수행할 동작, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 작업 단계를 수행할 횟수, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 작업 단계 출력을 쓸 파일 등의 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="81184-138">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="81184-139">**sysadmin** 고정 서버 역할의 멤버만 운영 체제 파일에 작업 단계 출력을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81184-139">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81184-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81184-140">See Also</span></span>  
 [<span data-ttu-id="81184-141">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="81184-141">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
