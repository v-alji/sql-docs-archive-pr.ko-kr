---
title: 패키지에 대한 SQL Server 에이전트 작업 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb9c1cf39ab5120958c33dfeff24588d59f71307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651081"
---
# <a name="sql-server-agent-jobs-for-packages"></a><span data-ttu-id="9e7fd-102">패키지에 대한 SQL Server 에이전트 작업</span><span class="sxs-lookup"><span data-stu-id="9e7fd-102">SQL Server Agent Jobs for Packages</span></span>
  <span data-ttu-id="9e7fd-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 실행을 자동화하고 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-103">You can automate and schedule the execution of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="9e7fd-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소 및 파일 시스템에 저장된 패키지를 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-104">You can schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, and are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="9e7fd-105">이 항목의 섹션</span><span class="sxs-lookup"><span data-stu-id="9e7fd-105">Sections in This Topic</span></span>  
 <span data-ttu-id="9e7fd-106">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="9e7fd-107">SQL Server 에이전트에서 작업 예약</span><span class="sxs-lookup"><span data-stu-id="9e7fd-107">Scheduling jobs in SQL Server Agent</span></span>](#jobs)  
  
-   [<span data-ttu-id="9e7fd-108">Integration Services 패키지 일정 예약</span><span class="sxs-lookup"><span data-stu-id="9e7fd-108">Scheduling Integration Services packages</span></span>](#packages)  
  
-   [<span data-ttu-id="9e7fd-109">예약 패키지 문제 해결</span><span class="sxs-lookup"><span data-stu-id="9e7fd-109">Troubleshooting scheduled packages</span></span>](#trouble)  
  
##  <a name="scheduling-jobs-in-sql-server-agent"></a><a name="jobs"></a> <span data-ttu-id="9e7fd-110">Scheduling Jobs in SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="9e7fd-110">Scheduling Jobs in SQL Server Agent</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9e7fd-111">에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 실행하여 태스크를 자동화 및 예약할 수 있도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 설치하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-111">Agent is the service installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that lets you automate and schedule tasks by running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="9e7fd-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 실행되고 있어야만 작업이 자동으로 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running before jobs can run automatically.</span></span> <span data-ttu-id="9e7fd-113">자세한 내용은 [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-113">For more information, see [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="9e7fd-114">**SQL Server 에이전트** 노드는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스에 연결하면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 개체 탐색기에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-114">The **SQL Server Agent** node appears in Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9e7fd-115">되풀이 태스크를 자동화하려면 **새 작업** 대화 상자를 사용하여 작업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-115">To automate a recurring task, you create a job by using the **New Job** dialog box.</span></span> <span data-ttu-id="9e7fd-116">자세한 내용은 [작업 구현](../../ssms/agent/implement-jobs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-116">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="9e7fd-117">작업을 만든 후 하나 이상의 단계를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-117">After you create the job, you must add at least one step.</span></span> <span data-ttu-id="9e7fd-118">한 개의 작업은 각각 다른 태스크를 수행하는 여러 단계를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-118">A job can include multiple steps, and each step can perform a different task.</span></span> <span data-ttu-id="9e7fd-119">자세한 내용은 [Manage Job Steps](../../ssms/agent/manage-job-steps.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-119">For more information, see [Manage Job Steps](../../ssms/agent/manage-job-steps.md).</span></span>  
  
 <span data-ttu-id="9e7fd-120">작업 및 작업 단계를 만든 다음에는 작업을 실행하는 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-120">After you create the job and the job steps, you can create a schedule for running the job.</span></span> <span data-ttu-id="9e7fd-121">그러나 수동으로 실행되는 예약되지 않은 작업도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-121">However you can also create an unscheduled job that you run manually.</span></span> <span data-ttu-id="9e7fd-122">자세한 내용은 [일정을 만들고 작업에 연결](../../ssms/agent/create-and-attach-schedules-to-jobs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-122">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
 <span data-ttu-id="9e7fd-123">작업을 종료하거나 경고를 추가할 때 전자 메일 메시지를 보낼 운영자를 지정하는 등의 알림 옵션 설정으로 작업을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-123">You can enhance the job by setting notification options, such as specifying an operator to send an e-mail message to when the job finishes, or adding alerts.</span></span> <span data-ttu-id="9e7fd-124">자세한 내용은 [경고](../../ssms/agent/alerts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-124">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
##  <a name="scheduling-integration-services-packages"></a><a name="packages"></a> <span data-ttu-id="9e7fd-125">Scheduling Integration Services Packages</span><span class="sxs-lookup"><span data-stu-id="9e7fd-125">Scheduling Integration Services Packages</span></span>  
 <span data-ttu-id="9e7fd-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 만들어 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 예약한 경우 **SQL Server Integration Services 패키지**에 하나 이상의 단계를 추가하고 단계 유형을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-126">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to schedule [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you must add at least one step and set the type of the step to **SQL Server Integration Services Package**.</span></span> <span data-ttu-id="9e7fd-127">한 개의 작업은 각각 다른 패키지를 실행하는 여러 단계를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-127">A job can include multiple steps, and each step can run a different package.</span></span>  
  
 <span data-ttu-id="9e7fd-128">작업 단계에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행하는 것은 **dtexec** (dtexec.exe) 및 **DTExecUI** (dtexecui.exe) 유틸리티를 사용하여 패키지를 실행하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-128">Running an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package from a job step is like running a package by using the **dtexec** (dtexec.exe) and **DTExecUI** (dtexecui.exe) utilities.</span></span> <span data-ttu-id="9e7fd-129">명령줄 옵션 또는 **패키지 실행 유틸리티** 대화 상자를 사용하여 패키지의 런타임 옵션을 설정하는 대신 **새 작업 단계** 대화 상자에서 런타임 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-129">Instead of setting the run-time options for a package by using command-line options or the **Execute Package Utility** dialog box, you set the run-time options in the **New Job Step** dialog box.</span></span> <span data-ttu-id="9e7fd-130">패키지를 실행하는 옵션에 대한 자세한 내용은 [dtexec Utility](dtexec-utility.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-130">For more information about the options for running a package, see [dtexec Utility](dtexec-utility.md).</span></span>  
  
 <span data-ttu-id="9e7fd-131">자세한 내용은 [SQL Server 에이전트를 사용하여 패키지 예약](../schedule-a-package-by-using-sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-131">For more information, see [Schedule a Package by using SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="9e7fd-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 패키지를 실행하는 방법을 보여 주는 비디오는 MSDN 라이브러리의 비디오 홈페이지에서 [방법: SQL Server 에이전트를 사용하여 패키지 실행 자동화(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=141771)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-132">For a video that demonstrates how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a package, see the video home page, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library.</span></span>  
  
##  <a name="troubleshooting"></a><a name="trouble"></a> <span data-ttu-id="9e7fd-133">문제 해결</span><span class="sxs-lookup"><span data-stu-id="9e7fd-133">Troubleshooting</span></span>  
 <span data-ttu-id="9e7fd-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 커맨드 라인에서 패키지가 성공적으로 실행되더라도 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에이전트 작업 단계를 시작하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-134">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step may fail to start a package even though the package runs successfully in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and from the command line.</span></span> <span data-ttu-id="9e7fd-135">이 문제에 대한 몇 가지 일반적인 이유와 권장 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-135">There are some common reasons for this issue and several recommended solutions.</span></span> <span data-ttu-id="9e7fd-136">자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-136">For more information, see the following resources.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9e7fd-137">기술 자료 문서 - [SQL Server 에이전트 작업 단계에서 SSIS 패키지를 호출할 때 SSIS 패키지가 실행되지 않는다](https://support.microsoft.com/kb/918760)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-137">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760)</span></span>  
  
-   <span data-ttu-id="9e7fd-138">MSDN Library의 비디오 - [문제 해결: SQL Server 에이전트를 사용하여 패키지 실행(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=141772).</span><span class="sxs-lookup"><span data-stu-id="9e7fd-138">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library.</span></span>  
  
 <span data-ttu-id="9e7fd-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에서 패키지를 시작한 후에 패키지 실행이 실패하거나 패키지가 성공적으로 실행되더라도 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-139">After a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step starts a package, the package execution may fail or the package may run successfully but with unexpected results.</span></span> <span data-ttu-id="9e7fd-140">이 문제를 해결하려면 다음 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-140">You can use the following tools to troubleshoot these issues.</span></span>  
  
-   <span data-ttu-id="9e7fd-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB 데이터베이스, [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소 또는 로컬 컴퓨터의 폴더에 저장된 패키지는 **로그 파일 뷰어** 뿐만 아니라 패키지 실행 중 생성된 로그 및 디버그 덤프 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-141">For packages that are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, or in a folder on your local machine, you can use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span>  
  
     <span data-ttu-id="9e7fd-142">**로그 파일 뷰어를 사용하려면 다음을 수행합니다.**</span><span class="sxs-lookup"><span data-stu-id="9e7fd-142">**To use the Log File Viewer, do the following.**</span></span>  
  
    1.  <span data-ttu-id="9e7fd-143">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 마우스 오른쪽 단추로 누르고 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-143">Right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in Object Explorer and then click **View History**.</span></span>  
  
    2.  <span data-ttu-id="9e7fd-144">**메시지** 열에 **작업이 실패했습니다.** 메시지가 있는 **로그 파일 요약** 상자에서 작업 실행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-144">Locate the job execution in the **Log file summary** box with the **job failed** message in the **Message** column.</span></span>  
  
    3.  <span data-ttu-id="9e7fd-145">작업 노드를 확장하고 작업 단계를 클릭하여 **로그 파일 요약** 상자 아래 영역에서 메시지의 세부 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-145">Expand the job node, and click the job step to view the details of the message in the area below the **Log file summary** box.</span></span>  
  
-   <span data-ttu-id="9e7fd-146">SSISDB 데이터베이스에 저장된 패키지에 대해서도 **로그 파일 뷰어** 뿐만 아니라 패키지 실행 중 생성된 로그 및 디버그 덤프 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-146">For packages that are stored in the SSISDB database, you can also use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span> <span data-ttu-id="9e7fd-147">또한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 대한 보고서를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-147">In addition, you can use the reports for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="9e7fd-148">**보고서에서 작업 실행과 연결된 패키지 실행에 대한 정보를 찾으려면 다음을 수행합니다.**</span><span class="sxs-lookup"><span data-stu-id="9e7fd-148">**To find information in the reports for the package execution associated with a job execution, do the following.**</span></span>  
  
    1.  <span data-ttu-id="9e7fd-149">위의 단계별 지침에 따라 작업 단계에 대한 자세한 메시지를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-149">Follow the steps above to view the details of the message for the job step.</span></span>  
  
    2.  <span data-ttu-id="9e7fd-150">메시지에 나열된 실행 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-150">Locate the Execution ID listed in the message.</span></span>  
  
    3.  <span data-ttu-id="9e7fd-151">개체 탐색기에서 Integration Services 카탈로그 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-151">Expand the Integration Services Catalog node in Object Explorer.</span></span>  
  
    4.  <span data-ttu-id="9e7fd-152">SSISDB를 마우스 오른쪽 단추로 클릭하고 보고서, 표준 보고서를 차례로 가리킨 다음 모든 실행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-152">Right-click SSISDB, point to Reports, then Standard Reports, and then click All Executions.</span></span>  
  
    5.  <span data-ttu-id="9e7fd-153">**모든 실행** 보고서의 **ID** 열에서 실행 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-153">In the **All Executions** report, locate the Execution ID in the **ID** column.</span></span> <span data-ttu-id="9e7fd-154">패키지 실행에 대한 정보를 보려면 **개요**, **모든 메시지**또는 **실행 성능** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-154">Click **Overview**, **All Messages**, or **Execution Performance** to view information about this package execution.</span></span>  
  
         <span data-ttu-id="9e7fd-155">개요, 모든 메시지 및 실행 성능 보고서에 대한 자세한 내용은 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="9e7fd-155">For more information about the Overview, All Messages, and Execution Performance reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9e7fd-156">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="9e7fd-156">External Resources</span></span>  
  
-   <span data-ttu-id="9e7fd-157">[웹 사이트의 기술 자료 문서 -](https://support.microsoft.com/kb/918760)SQL Server 에이전트 작업 단계에서 SSIS 패키지를 호출할 때 SSIS 패키지가 실행되지 않는다 [!INCLUDE[msCoName](../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7fd-157">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760), on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site</span></span>  
  
-   <span data-ttu-id="9e7fd-158">MSDN Library의 비디오 - [문제 해결: SQL Server 에이전트를 사용하여 패키지 실행(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=141772)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-158">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="9e7fd-159">MSDN Library의 비디오 - [방법: SQL Server 에이전트를 사용하여 패키지 실행 자동화(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=141771)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-159">Video, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="9e7fd-160">mssqltips.com의 기술 문서 - [Windows PowerShell을 사용하여 SQL Server 에이전트 작업 확인(Checking SQL Server Agent jobs using Windows PowerShell)](https://go.microsoft.com/fwlink/?LinkId=165675)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-160">Technical article, [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="9e7fd-161">mssqltips.com의 기술 문서 - [SQL 에이전트 작업 설정 또는 해제 시 자동 경고](https://go.microsoft.com/fwlink/?LinkId=165676)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-161">Technical article, [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="9e7fd-162">mssqltips.com의 블로그 항목 - [Windows 이벤트 로그에 쓰도록 SQL 에이전트 작업 구성](https://go.microsoft.com/fwlink/?LinkId=220745)</span><span class="sxs-lookup"><span data-stu-id="9e7fd-162">Blog entry, [Configuring SQL Agent Jobs to Write to Windows Event Log](https://go.microsoft.com/fwlink/?LinkId=220745), on mssqltips.com.</span></span>  
  
  
