---
title: CmdExec 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c557b8ea4228d27b73d361c50aac62232d1e00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650354"
---
# <a name="create-a-cmdexec-job-step"></a><span data-ttu-id="57ac5-102">CmdExec 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="57ac5-102">Create a CmdExec Job Step</span></span>
  <span data-ttu-id="57ac5-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SQL Server 관리 개체 또는을 사용 하 여 실행 프로그램 또는 운영 체제 명령을 사용 하는 에이전트 작업 단계를 만들고 정의 하는 방법에 대해 설명 합니다 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57ac5-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that uses an executable program or operating system command by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="57ac5-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="57ac5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="57ac5-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="57ac5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="57ac5-106">보안</span><span class="sxs-lookup"><span data-stu-id="57ac5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="57ac5-107">**CmdExec 작업 단계를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="57ac5-107">**To create a CmdExec job step, using:**</span></span>  
  
     [<span data-ttu-id="57ac5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="57ac5-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="57ac5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="57ac5-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="57ac5-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="57ac5-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="57ac5-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="57ac5-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="57ac5-112">보안</span><span class="sxs-lookup"><span data-stu-id="57ac5-112">Security</span></span>  
 <span data-ttu-id="57ac5-113">기본적으로 **sysadmin** 고정 서버 역할의 멤버만 CmdExec 작업 단계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-113">By default, only members of the **sysadmin** fixed server role can create CmdExec job steps.</span></span> <span data-ttu-id="57ac5-114">**sysadmin** 사용자가 프록시 계정을 만들지 않으면 이 작업 단계들은 SQL Server 에이전트 서비스 계정의 컨텍스트로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-114">These job steps run under the context of the SQL Server Agent service account unless the **sysadmin** user creates a proxy account.</span></span> <span data-ttu-id="57ac5-115">**sysadmin** 역할의 멤버가 아니더라도 CmdExec 프록시 계정에 액세스할 수 있는 사용자는 CmdExec 작업 단계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-115">Users who are not members of the **sysadmin** role can create CmdExec job steps if they have access to a CmdExec proxy account.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="57ac5-116">권한</span><span class="sxs-lookup"><span data-stu-id="57ac5-116">Permissions</span></span>  
 <span data-ttu-id="57ac5-117">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57ac5-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="57ac5-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="57ac5-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="57ac5-119">CmdExec 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="57ac5-119">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="57ac5-120">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="57ac5-121">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-121">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="57ac5-122">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-122">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="57ac5-123">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-123">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="57ac5-124">**유형** 목록에서 **운영 체제(CmdExec)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-124">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
6.  <span data-ttu-id="57ac5-125">**다음 계정으로 실행** 목록에서 해당 작업이 사용할 자격 증명을 가진 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-125">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="57ac5-126">기본적으로 CmdExec 작업 단계는 SQL Server 에이전트 서비스 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-126">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
7.  <span data-ttu-id="57ac5-127">**성공한 명령의 프로세스 종료 코드** 상자에 0에서 999999까지의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-127">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
8.  <span data-ttu-id="57ac5-128">**명령** 입력란에 운영 체제 명령이나 실행 프로그램을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-128">In the **Command** box, enter the operating system command or executable program.</span></span> <span data-ttu-id="57ac5-129">예를 보려면 "Transact T-SQL 사용"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57ac5-129">See "Using Transact T-SQL for an example.</span></span>  
  
9. <span data-ttu-id="57ac5-130">**고급** 페이지를 클릭하여 작업 단계의 성공 또는 실패 여부에 따라 수행할 동작, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계를 수행할 횟수, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계 출력을 쓸 파일 등의 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-130">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="57ac5-131">**sysadmin** 고정 서버 역할의 멤버만 운영 체제 파일에 작업 단계 출력을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-131">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="57ac5-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="57ac5-132">Using Transact-SQL</span></span>  
  
### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="57ac5-133">CmdExec 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="57ac5-133">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="57ac5-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="57ac5-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="57ac5-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="57ac5-137">자세한 내용은 [sp_add_jobstep &#40;transact-sql](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) 을 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="57ac5-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="57ac5-138">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="57ac5-138">Using SQL Server Management Objects</span></span>  

### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="57ac5-139">CmdExec 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="57ac5-139">To create a CmdExec job step</span></span>
  
 <span data-ttu-id="57ac5-140">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57ac5-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
