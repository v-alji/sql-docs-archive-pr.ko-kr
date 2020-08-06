---
title: Transact-SQL 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b83ee944d2ca5c10ff1b77f3e6e6da6054b5c99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737473"
---
# <a name="create-a-transact-sql-job-step"></a><span data-ttu-id="60a65-102">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="60a65-102">Create a Transact-SQL Job Step</span></span>
  <span data-ttu-id="60a65-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 스크립트를 실행 하는 에이전트 작업 단계를 만드는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="60a65-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="60a65-104">작업 단계 스크립트는 저장 프로시저와 확장 저장 프로시저를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-104">These job step scripts may call stored procedures and extended stored procedures.</span></span> <span data-ttu-id="60a65-105">단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계에는 다수의 일괄 처리 및 GO 명령이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-105">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches and embedded GO commands.</span></span> <span data-ttu-id="60a65-106">작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60a65-106">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
 <span data-ttu-id="60a65-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="60a65-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="60a65-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="60a65-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="60a65-109">보안</span><span class="sxs-lookup"><span data-stu-id="60a65-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="60a65-110">**Transact-SQL 작업 단계를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="60a65-110">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="60a65-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60a65-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="60a65-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60a65-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="60a65-113">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="60a65-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="60a65-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="60a65-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="60a65-115">보안</span><span class="sxs-lookup"><span data-stu-id="60a65-115">Security</span></span>  
 <span data-ttu-id="60a65-116">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60a65-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="60a65-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="60a65-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="60a65-118">Transact-SQL 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="60a65-118">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="60a65-119">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="60a65-120">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-120">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="60a65-121">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-121">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="60a65-122">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-122">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="60a65-123">**유형** 목록에서 **T-SQL(Transact-SQL) 스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-123">In the **Type** list, click **Transact-SQL Script (TSQL)**.</span></span>  
  
6.  <span data-ttu-id="60a65-124">**명령** 상자에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령 일괄 처리를 입력하거나 **열기** 를 클릭하여 명령으로 사용할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-124">In the **Command** box, type the [!INCLUDE[tsql](../../includes/tsql-md.md)] command batches, or click **Open** to select a [!INCLUDE[tsql](../../includes/tsql-md.md)] file to use as the command.</span></span>  
  
7.  <span data-ttu-id="60a65-125">**구문 분석** 을 클릭하여 구문을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-125">Click **Parse** to check your syntax.</span></span>  
  
8.  <span data-ttu-id="60a65-126">구문이 정확하면 “구문 분석이 성공했습니다”라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-126">The message "Parse succeeded" is displayed when your syntax is correct.</span></span> <span data-ttu-id="60a65-127">오류가 발견되면 구문을 수정한 다음 작업을 계속 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="60a65-127">If an error is found, correct the syntax before continuing.</span></span>  
  
9. <span data-ttu-id="60a65-128">**고급** 페이지를 클릭하여 작업 단계의 성공 또는 실패 여부에 따라 수행할 동작, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계를 수행할 횟수, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계 출력을 쓸 파일이나 테이블 등의 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-128">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file or table where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="60a65-129">**sysadmin** 고정 서버 역할의 멤버만 운영 체제 파일에 작업 단계 출력을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-129">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span> <span data-ttu-id="60a65-130">모든 SQL Server 에이전트 사용자는 테이블에 출력을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-130">All SQL Server Agent users can log output to a table.</span></span>  
  
10. <span data-ttu-id="60a65-131">**sysadmin** 고정 서버 역할의 멤버이면서 이 작업 단계를 다른 SQL 로그인으로 실행하려는 경우 **다음 사용자 이름으로 실행** 목록에서 해당 SQL 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-131">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="60a65-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="60a65-132">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="60a65-133">Transact-SQL 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="60a65-133">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="60a65-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="60a65-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="60a65-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="60a65-137">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60a65-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="60a65-138">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="60a65-138">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="60a65-139">**Transact-SQL 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="60a65-139">**To create a Transact-SQL job step**</span></span>  
  
 <span data-ttu-id="60a65-140">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60a65-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
