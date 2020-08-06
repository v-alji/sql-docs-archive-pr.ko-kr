---
title: 작업 단계 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server replication]
- job steps [SQL Server Agent]
- jobs [SQL Server Agent], Integration Services package step
- executable programs as job steps
- operating systems [SQL Server], job steps
- Transact-SQL job step
- job steps [Transact-SQL]
- Integration Services packages, job steps
- replication job steps [SQL Server]
- logs [SQL Server], jobs
- SQL Server Agent jobs, job steps
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: 51352afc-a0a4-428b-8985-f9e58bb57c31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7362df13956e44b73d6984691e882bec2f39a1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652535"
---
# <a name="manage-job-steps"></a><span data-ttu-id="676db-102">작업 단계 관리</span><span class="sxs-lookup"><span data-stu-id="676db-102">Manage Job Steps</span></span>
  <span data-ttu-id="676db-103">작업 단계는 데이터베이스나 서버에서 작업이 수행하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="676db-103">A job step is an action that the job takes on a database or a server.</span></span> <span data-ttu-id="676db-104">모든 작업에는 작업 단계가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-104">Every job must have at least one job step.</span></span> <span data-ttu-id="676db-105">작업 단계가 될 수 있는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-105">Job steps can be:</span></span>  
  
-   <span data-ttu-id="676db-106">실행 프로그램 및 운영 체제 명령</span><span class="sxs-lookup"><span data-stu-id="676db-106">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="676db-107">문(저장 프로시저 및 확장 저장 프로시저 포함)</span><span class="sxs-lookup"><span data-stu-id="676db-107">statements, including stored procedures and extended stored procedures.</span></span>  
  
-   <span data-ttu-id="676db-108">PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="676db-108">PowerShell scripts.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="676db-109">ActiveX 스크립트</span><span class="sxs-lookup"><span data-stu-id="676db-109">ActiveX scripts.</span></span>  
  
-   <span data-ttu-id="676db-110">복제 태스크</span><span class="sxs-lookup"><span data-stu-id="676db-110">Replication tasks.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="676db-111">태스크</span><span class="sxs-lookup"><span data-stu-id="676db-111">tasks.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="676db-112">패키지</span><span class="sxs-lookup"><span data-stu-id="676db-112">packages.</span></span>  
  
 <span data-ttu-id="676db-113">모든 작업 단계는 특정 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-113">Every job step runs in a specific security context.</span></span> <span data-ttu-id="676db-114">작업 단계에서 프록시를 지정하면 해당 작업 단계는 프록시의 자격 증명 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-114">If the job step specifies a proxy, the job step runs in the security context of the credential for the proxy.</span></span> <span data-ttu-id="676db-115">작업 단계에서 프록시를 지정하지 않으면 작업 단계는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-115">If a job step does not specify a proxy, the job step runs in the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account.</span></span> <span data-ttu-id="676db-116">sysadmin 고정 서버 역할의 멤버만이 프록시를 명시적으로 지정하지 않는 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-116">Only members of the sysadmin fixed server role can create jobs that do not explicitly specify a proxy.</span></span>  
  
 <span data-ttu-id="676db-117">작업 단계는 특정 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자의 컨텍스트에서 실행되기 때문에 해당 사용자는 작업 단계를 실행하는 데 필요한 권한과 구성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-117">Because job steps run in the context of a specific [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user, that user must have the permissions and configuration necessary for the job step to execute.</span></span> <span data-ttu-id="676db-118">예를 들어 드라이브 문자나 UNC(Universal Naming Convention) 경로가 필요한 작업을 만드는 경우 작업 단계는 태스크를 테스트하는 동안 사용자의 Windows 사용자 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-118">For example, if you create a job that requires a drive letter or a Universal Naming Convention (UNC) path, the job steps may run under your Windows user account while testing the tasks.</span></span> <span data-ttu-id="676db-119">그러나 해당 작업 단계의 Windows 사용자도 필요한 권한, 드라이브 문자 구성 또는 필요한 드라이브에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-119">However, the Windows user for the job step must also have the necessary permissions, drive letter configurations, or access to the required drive.</span></span> <span data-ttu-id="676db-120">그렇지 않으면 작업 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-120">Otherwise, the job step fails.</span></span> <span data-ttu-id="676db-121">이런 문제가 발생하지 않도록 각 작업 단계의 프록시에 작업 단계에서 수행하는 태스크에 필요한 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="676db-121">To prevent this problem, ensure that the proxy for each job step has the necessary permissions for the task that the job step performs.</span></span> <span data-ttu-id="676db-122">자세한 내용은 [SQL Server 데이터베이스 엔진 및 Azure SQL Database에 대 한 Security Center](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-122">For more information, see [Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).</span></span>  
  
## <a name="job-step-logs"></a><span data-ttu-id="676db-123">작업 단계 로그</span><span class="sxs-lookup"><span data-stu-id="676db-123">Job Step Logs</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="676db-124">에이전트에서는 일부 작업 단계의 출력을 운영 체제 파일이나 msdb 데이터베이스의 sysjobstepslogs 테이블에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-124">Agent can write output from some job steps either to an operating system file or to the sysjobstepslogs table in the msdb database.</span></span> <span data-ttu-id="676db-125">다음은 두 대상에 모두 출력을 기록할 수 있는 작업 단계 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="676db-125">The following job step types can write output to both destinations:</span></span>  
  
-   <span data-ttu-id="676db-126">실행 프로그램 및 운영 체제 명령</span><span class="sxs-lookup"><span data-stu-id="676db-126">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="676db-127">문.</span><span class="sxs-lookup"><span data-stu-id="676db-127">statements.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="676db-128">태스크</span><span class="sxs-lookup"><span data-stu-id="676db-128">tasks.</span></span>  
  
 <span data-ttu-id="676db-129">sysadmin 고정 서버 역할의 멤버인 사용자가 실행한 작업 단계만 작업 단계 출력을 운영 체제 파일에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-129">Only job steps that are executed by users who are members of the sysadmin fixed server role can write job step output to operating system files.</span></span> <span data-ttu-id="676db-130">msdb 데이터베이스에서 SQLAgentUserRole, SQLAgentReaderRole 또는 SQLAgentOperatorRole 고정 데이터베이스 역할의 멤버인 사용자가 작업 단계를 실행할 경우 이러한 작업 단계의 출력은 sysjobstepslogs 테이블에만 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-130">If job steps are executed by users who are members of the SQLAgentUserRole, SQLAgentReaderRole, or the SQLAgentOperatorRole fixed database roles in the msdb database, then the output from these job steps can be written only to the sysjobstepslogs table.</span></span>  
  
 <span data-ttu-id="676db-131">작업이나 작업 단계가 삭제되면 자동으로 작업 단계 로그가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-131">Job step logs are automatically deleted when jobs or job steps are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="676db-132">복제 태스크와 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 작업 단계 로깅은 해당 하위 시스템에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-132">Replication task and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step logging is handled by their respective subsystem.</span></span> <span data-ttu-id="676db-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 이러한 유형의 작업 단계에 대한 작업 단계 로깅을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-133">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to configure jog step logging for these types of job steps.</span></span>  
  
## <a name="executable-programs-and-operating-system-commands-as-job-steps"></a><span data-ttu-id="676db-134">실행 프로그램 및 운영 체제 명령을 작업 단계로 사용</span><span class="sxs-lookup"><span data-stu-id="676db-134">Executable Programs and Operating-System Commands As Job Steps</span></span>  
 <span data-ttu-id="676db-135">실행 프로그램과 운영 체제 명령을 작업 단계로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-135">Executable programs and operating-system commands can be used as job steps.</span></span> <span data-ttu-id="676db-136">이러한 파일의 확장명은 .bat, .cmd, .com 또는 .exe입니다.</span><span class="sxs-lookup"><span data-stu-id="676db-136">These files may have .bat, .cmd, .com, or .exe file extensions.</span></span>  
  
 <span data-ttu-id="676db-137">실행 프로그램이나 운영 체제 명령을 작업 단계로 사용할 경우에는 다음을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-137">When you use an executable program or an operating-system command as a job step, you must specify:</span></span>  
  
-   <span data-ttu-id="676db-138">명령이 성공한 경우 반환되는 프로세스 종료 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-138">The process exit code returned if the command was successful.</span></span>  
  
-   <span data-ttu-id="676db-139">실행할 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="676db-139">The command to execute.</span></span> <span data-ttu-id="676db-140">운영 체제 명령을 실행하려면 명령 자체를 지정하면 되고</span><span class="sxs-lookup"><span data-stu-id="676db-140">To execute an operating system command, this is simply the command itself.</span></span> <span data-ttu-id="676db-141">외부 프로그램을 실행하려면 프로그램 이름과 프로그램 인수를 지정합니다(예: **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**).</span><span class="sxs-lookup"><span data-stu-id="676db-141">For an external program, this is the name of the program and the arguments to the program, for example: **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="676db-142">실행 파일이 시스템 경로나 작업 단계가 실행되는 계정의 사용자 경로에 지정된 디렉터리에 있지 않은 경우 실행 파일의 전체 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-142">You must provide the full path to the executable if the executable is not located in a directory specified in the system path or the path for the user that the job step runs as.</span></span>  
  
## <a name="transact-sql-job-steps"></a><span data-ttu-id="676db-143">Transact-SQL 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-143">Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="676db-144">[!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계를 만들 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-144">When you create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step, you must:</span></span>  
  
-   <span data-ttu-id="676db-145">작업을 실행하는 데이터베이스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-145">Identify the database in which to run the job.</span></span>  
  
-   <span data-ttu-id="676db-146">실행할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-146">Type the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute.</span></span> <span data-ttu-id="676db-147">이 문에서 저장 프로시저나 확장 저장 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-147">The statement may call a stored procedure or an extended stored procedure.</span></span>  
  
 <span data-ttu-id="676db-148">필요에 따라 기존의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 파일을 작업 단계에 대한 명령으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-148">Optionally, you can open an existing [!INCLUDE[tsql](../../includes/tsql-md.md)] file as the command for the job step.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="676db-149">작업 단계에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 프록시를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-149">job steps do not use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span> <span data-ttu-id="676db-150">대신에 작업 단계가 작업 단계 소유자의 계정으로 실행되거나 작업 단계 소유자가 sysadmin 고정 서버 역할의 멤버인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-150">Instead, the job step runs as the owner of the job step, or as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account if the owner of the job step is a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="676db-151">sysadmin 고정 서버 역할의 멤버는 sp_add_jobstep 저장 프로시저의 [!INCLUDE[tsql](../../includes/tsql-md.md)] database_user_name *매개 변수를 사용하여* 작업 단계가 다른 사용자의 컨텍스트에서 실행되도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-151">Members of the sysadmin fixed server role can also specify that [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps run under the context of another user by using the *database_user_name* parameter of the sp_add_jobstep stored procedure.</span></span> <span data-ttu-id="676db-152">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-152">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="676db-153">단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계에는 다수의 일괄 처리가 여러 개 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-153">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="676db-154">작업 단계에는 포함된 GO 명령이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-154">job steps can contain embedded GO commands.</span></span>  
  
## <a name="powershell-scripting-job-steps"></a><span data-ttu-id="676db-155">PowerShell 스크립팅 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-155">PowerShell Scripting Job Steps</span></span>  
 <span data-ttu-id="676db-156">PowerShell 스크립트 작업 단계를 만들 때 다음 둘 중 하나를 단계에 대한 명령으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-156">When you create a PowerShell script job step, you must specify one of two things as the command for the step:</span></span>  
  
-   <span data-ttu-id="676db-157">PowerShell 스크립트 텍스트</span><span class="sxs-lookup"><span data-stu-id="676db-157">The text of a PowerShell script.</span></span>  
  
-   <span data-ttu-id="676db-158">열려는 기존 PowerShell 스크립트 파일</span><span class="sxs-lookup"><span data-stu-id="676db-158">An existing PowerShell script file to be opened.</span></span>  
  
 <span data-ttu-id="676db-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트 powershell 하위 시스템은 powershell 세션을 열고 powershell 스냅인을 로드 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 작업 단계 명령으로 사용 되는 PowerShell 스크립트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell 공급자 및 cmdlet을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-159">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell subsystem opens a PowerShell session and loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins. The PowerShell script used as the job step command can reference the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span> <span data-ttu-id="676db-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 스냅인을 사용하여 PowerShell 스크립트를 작성하는 방법에 대한 자세한 내용은 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-160">For more information about writing PowerShell scripts using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins, see the [SQL Server PowerShell](../../powershell/sql-server-powershell.md).</span></span>  
  
## <a name="activex-scripting-job-steps"></a><span data-ttu-id="676db-161">ActiveX 스크립팅 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-161">ActiveX Scripting Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="676db-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 이후 버전에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트에서 ActiveX 스크립팅 작업 단계가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-162">The ActiveX scripting job step will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="676db-163">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-163">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="676db-164">ActiveX 스크립팅 작업 단계를 만들 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-164">When you create an ActiveX scripting job step, you must:</span></span>  
  
-   <span data-ttu-id="676db-165">작업 단계를 작성하는 스크립트 언어를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-165">Identify the scripting language in which the job step is written.</span></span>  
  
-   <span data-ttu-id="676db-166">ActiveX 스크립트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-166">Write the ActiveX script.</span></span>  
  
 <span data-ttu-id="676db-167">기존 ActiveX 스크립트 파일을 작업 단계에 대한 명령으로 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-167">You can also open an existing ActiveX script file as the command for the job step.</span></span> <span data-ttu-id="676db-168">또한 Microsoft Visual Basic 등을 사용하여 ActiveX 스크립트 명령을 외부에서 컴파일한 다음 실행 프로그램으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-168">Alternatively, ActiveX script commands can be externally compiled (for example, using Microsoft Visual Basic) and then run as executable programs.</span></span>  
  
 <span data-ttu-id="676db-169">작업 단계 명령이 ActiveX 스크립트이면 SQLActiveScriptHost 개체를 사용하여 출력을 작업 단계 기록 로그로 인쇄하거나 COM 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-169">When a job step command is an ActiveX script, you can use the SQLActiveScriptHost object to print output to the job step history log or create COM objects.</span></span> <span data-ttu-id="676db-170">SQLActiveScriptHost는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 호스팅 시스템에서 스크립트 네임스페이스로 도입되는 전역 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="676db-170">SQLActiveScriptHost is a global object that is introduced by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent hosting system into the script name space.</span></span> <span data-ttu-id="676db-171">이 개체에는 두 가지 메서드(Print 및 CreateObject)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-171">The object has two methods (Print and CreateObject).</span></span> <span data-ttu-id="676db-172">다음 예에서는 VBScript(Visual Basic Scripting Edition)에서 ActiveX 스크립팅이 작동하는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="676db-172">The following example shows how ActiveX scripting works in Visual Basic Scripting Edition (VBScript).</span></span>  
  
```  
' VBScript example for ActiveX Scripting job step  
' Create a Dmo.Server object. The object connects to the  
' server on which the script is running.  
  
Set oServer = CreateObject("SQLDmo.SqlServer")  
oServer.LoginSecure = True  
oServer.Connect "(local)"  
'Disconnect and destroy the server object  
oServer.DisConnect  
Set oServer = nothing
```  
  
## <a name="replication-job-steps"></a><span data-ttu-id="676db-173">복제 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-173">Replication Job Steps</span></span>  
 <span data-ttu-id="676db-174">복제를 사용하여 게시와 구독을 만드는 경우 기본적으로 복제 작업이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="676db-174">When you create publications and subscriptions using replication, replication jobs are created by default.</span></span> <span data-ttu-id="676db-175">만들어지는 작업 유형은 복제 유형(스냅샷, 트랜잭션 또는 병합)과 사용되는 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="676db-175">The type of job created is determined by the type of replication (snapshot, transactional, or merge) and the options used.</span></span>  
  
 <span data-ttu-id="676db-176">복제 작업 단계는 다음 복제 에이전트 중 하나를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-176">Replication job steps activate one of these replication agents:</span></span>  
  
-   <span data-ttu-id="676db-177">스냅샷 에이전트(Snapshot 작업)</span><span class="sxs-lookup"><span data-stu-id="676db-177">Snapshot Agent (Snapshot job)</span></span>  
  
-   <span data-ttu-id="676db-178">로그 판독기 에이전트(LogReader 작업)</span><span class="sxs-lookup"><span data-stu-id="676db-178">Log Reader Agent (LogReader job)</span></span>  
  
-   <span data-ttu-id="676db-179">배포 에이전트(Distribution 작업)</span><span class="sxs-lookup"><span data-stu-id="676db-179">Distribution Agent (Distribution job)</span></span>  
  
-   <span data-ttu-id="676db-180">병합 에이전트(Merge 작업)</span><span class="sxs-lookup"><span data-stu-id="676db-180">Merge Agent (Merge job)</span></span>  
  
-   <span data-ttu-id="676db-181">큐 판독기 에이전트(QueueReader 작업)</span><span class="sxs-lookup"><span data-stu-id="676db-181">Queue Reader Agent (QueueReader job)</span></span>  
  
 <span data-ttu-id="676db-182">복제를 설정할 때 복제 에이전트 실행 방법을 지정할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 시작 후 복제 에이전트가 연속해서 실행되도록 하거나, 요청 시 실행하거나, 일정에 따라 실행하는 세 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-182">When replication is set up, you can specify to run the replication agents in one of three ways: continuously after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is started, on demand, or according to a schedule.</span></span> <span data-ttu-id="676db-183">복제 에이전트에 대한 자세한 내용은 [복제 에이전트 개요](../../relational-databases/replication/agents/replication-agents-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-183">For more information about replication agents, see [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md).</span></span>  
  
## <a name="analysis-services-job-steps"></a><span data-ttu-id="676db-184">Analysis Services 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-184">Analysis Services Job Steps</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="676db-185">에이전트는 명령 작업 단계와 쿼리 작업 단계라는 서로 다른 유형의 두 가지 Analysis Services 작업 단계를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-185">Agent supports two distinct types of Analysis Services job steps, command job steps, and query job steps.</span></span>  
  
### <a name="analysis-services-command-job-steps"></a><span data-ttu-id="676db-186">Analysis Services 명령 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-186">Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="676db-187">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 명령 작업 단계를 만들 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-187">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] command job step, you must:</span></span>  
  
-   <span data-ttu-id="676db-188">작업 단계를 실행할 데이터베이스 OLAP 서버를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-188">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="676db-189">실행할 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-189">Type the statement to execute.</span></span> <span data-ttu-id="676db-190">문은 XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** 메서드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-190">The statement must be an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** method.</span></span> <span data-ttu-id="676db-191">전체 SOAP Envelope 또는 XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** 메서드를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-191">The statement may not contain a complete SOAP envelope or an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** method.</span></span> <span data-ttu-id="676db-192">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 전체 SOAP Envelope와 **Discover** 메서드를 지원하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에서는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-192">Notice that, while [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span>  
  
### <a name="analysis-services-query-job-steps"></a><span data-ttu-id="676db-193">Analysis Services 쿼리 작업 단계</span><span class="sxs-lookup"><span data-stu-id="676db-193">Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="676db-194">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 쿼리 작업 단계를 만들 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-194">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] query job step, you must:</span></span>  
  
-   <span data-ttu-id="676db-195">작업 단계를 실행할 데이터베이스 OLAP 서버를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-195">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="676db-196">실행할 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-196">Type the statement to execute.</span></span> <span data-ttu-id="676db-197">이 문은 MDX(Multidimensional Expressions) 쿼리여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-197">The statement must be a multidimensional expressions (MDX) query.</span></span>  
  
 <span data-ttu-id="676db-198">MDX에 대 한 자세한 내용은 [Mdx 쿼리 기본 사항 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-198">For more information on MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
## <a name="integration-services-packages"></a><span data-ttu-id="676db-199">Integration Services 패키지</span><span class="sxs-lookup"><span data-stu-id="676db-199">Integration Services Packages</span></span>  
 <span data-ttu-id="676db-200">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 작업 단계를 만들 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-200">When you create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step, you must do the following:</span></span>  
  
-   <span data-ttu-id="676db-201">패키지 원본을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-201">Identify the source of the package.</span></span>  
  
-   <span data-ttu-id="676db-202">패키지 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-202">Identify the location of the package.</span></span>  
  
-   <span data-ttu-id="676db-203">패키지에 구성 파일이 필요한 경우 구성 파일을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-203">If configuration files are required for the package, identify the configuration files.</span></span>  
  
-   <span data-ttu-id="676db-204">패키지에 명령 파일이 필요한 경우 명령 파일을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-204">If command files are required for the package, identify the command files.</span></span>  
  
-   <span data-ttu-id="676db-205">패키지에 사용할 확인 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-205">Identify the verification to use for the package.</span></span> <span data-ttu-id="676db-206">예를 들어 패키지에 서명이나 특정 패키지 ID가 필요하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-206">For example, you can specify that the package must be signed, or that the package must have a specific package ID.</span></span>  
  
-   <span data-ttu-id="676db-207">패키지의 데이터 원본을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-207">Identify the data sources for the package.</span></span>  
  
-   <span data-ttu-id="676db-208">패키지의 로그 공급자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-208">Identify the log providers for the package.</span></span>  
  
-   <span data-ttu-id="676db-209">패키지를 실행하기 전에 설정할 변수와 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-209">Specify variables and values to set before running the package.</span></span>  
  
-   <span data-ttu-id="676db-210">실행 옵션을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-210">Identify execution options.</span></span>  
  
-   <span data-ttu-id="676db-211">명령줄 옵션을 추가하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-211">Add or modify command-line options.</span></span>  
  
 <span data-ttu-id="676db-212">SSIS 카탈로그에 패키지를 배포하고 패키지 원본으로 **SSIS 카탈로그** 를 지정한 경우 이러한 구성 정보의 상당 부분은 패키지에서 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="676db-212">Note that if you deployed the package to the SSIS Catalog and you specify **SSIS Catalog** as the package source, much of this configuration information is obtained automatically from the package.</span></span> <span data-ttu-id="676db-213">**구성** 탭에서 환경, 매개 변수 값, 연결 관리자 값, 속성 무효화 및 패키지가 32비트 런타임 환경에서 실행되는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="676db-213">Under the **Configuration** tab you can specify the environment, parameter values, connection manager values, property overrides, and whether the package runs in a 32-bit runtime environment.</span></span>  
  
 <span data-ttu-id="676db-214">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행하는 작업 단계 만들기에 대한 자세한 내용은 [패키지에 대한 SQL Server 에이전트 작업](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="676db-214">For more information about creating job steps that run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="676db-215">관련 작업</span><span class="sxs-lookup"><span data-stu-id="676db-215">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="676db-216">**설명**</span><span class="sxs-lookup"><span data-stu-id="676db-216">**Description**</span></span>|<span data-ttu-id="676db-217">**항목**</span><span class="sxs-lookup"><span data-stu-id="676db-217">**Topic**</span></span>|  
|<span data-ttu-id="676db-218">실행 프로그램으로 작업 단계를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-218">Describes how to create a job step with an executable program.</span></span>|[<span data-ttu-id="676db-219">CmdExec 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="676db-219">Create a CmdExec Job Step</span></span>](create-a-cmdexec-job-step.md)|  
|<span data-ttu-id="676db-220">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 사용 권한을 다시 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-220">Describes how to reset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent permissions.</span></span>|[<span data-ttu-id="676db-221">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="676db-221">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>](configure-a-user-to-create-and-manage-sql-server-agent-jobs.md)|  
|<span data-ttu-id="676db-222">[!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-222">Describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step.</span></span>|[<span data-ttu-id="676db-223">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="676db-223">Create a Transact-SQL Job Step</span></span>](create-a-transact-sql-job-step.md)|  
|<span data-ttu-id="676db-224">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 Transact-SQL 작업 단계의 옵션을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-224">Describes how to define options for Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Transact-SQL job steps.</span></span>|[<span data-ttu-id="676db-225">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="676db-225">Define Transact-SQL Job Step Options</span></span>](define-transact-sql-job-step-options.md)|  
|<span data-ttu-id="676db-226">ActiveX 스크립트 작업 단계를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-226">Describes how to create an ActiveX script job step.</span></span>|[<span data-ttu-id="676db-227">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="676db-227">Create an ActiveX Script Job Step</span></span>](create-an-activex-script-job-step.md)|  
|<span data-ttu-id="676db-228">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services 명령과 쿼리를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계를 만들고 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-228">Describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries.</span></span>|[<span data-ttu-id="676db-229">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="676db-229">Create an Analysis Services Job Step</span></span>](create-an-analysis-services-job-step.md)|  
|<span data-ttu-id="676db-230">작업 실행 중에 오류가 발생하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 수행해야 하는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-230">Describes what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span>|[<span data-ttu-id="676db-231">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="676db-231">Set Job Step Success or Failure Flow</span></span>](set-job-step-success-or-failure-flow.md)|  
|<span data-ttu-id="676db-232">작업 단계 속성 대화 상자에서 작업 단계의 세부 사항을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-232">Describes how to view job step details in the Job Step Properties dialog.</span></span>|[<span data-ttu-id="676db-233">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="676db-233">View Job Step Information</span></span>](view-job-step-information.md)|  
|<span data-ttu-id="676db-234">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계 로그를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="676db-234">Describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>|[<span data-ttu-id="676db-235">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="676db-235">Delete a Job Step Log</span></span>](delete-a-job-step-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="676db-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="676db-236">See Also</span></span>  
 <span data-ttu-id="676db-237">[dbo.sysjobstepslogs &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="676db-237">[dbo.sysjobstepslogs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span></span>  
 <span data-ttu-id="676db-238">[작업 만들기](create-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="676db-238">[Create Jobs](create-jobs.md) </span></span>  
 [<span data-ttu-id="676db-239">sp_add_job&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="676db-239">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
