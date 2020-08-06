---
title: PowerShell 스크립트 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4232cdfa584fdcc2e13786ecc9bd00f0c6fe7066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650356"
---
# <a name="create-a-powershell-script-job-step"></a><span data-ttu-id="89950-102">Create a PowerShell Script Job Step</span><span class="sxs-lookup"><span data-stu-id="89950-102">Create a PowerShell Script Job Step</span></span>
  <span data-ttu-id="89950-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 PowerShell 스크립트를 실행하는 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 작업 단계를 만들고 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-103">This topic describes how to create and define a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes a PowerShell script in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="89950-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="89950-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="89950-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="89950-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="89950-106">보안</span><span class="sxs-lookup"><span data-stu-id="89950-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="89950-107">**PowerShell 스크립트 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="89950-107">**To create a PowerShell Script job step, using:**</span></span>  
  
     [<span data-ttu-id="89950-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="89950-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="89950-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="89950-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="89950-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="89950-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="89950-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="89950-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="89950-112">보안</span><span class="sxs-lookup"><span data-stu-id="89950-112">Security</span></span>  
 <span data-ttu-id="89950-113">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89950-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="89950-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="89950-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="89950-115">PowerShell 스크립트 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="89950-115">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="89950-116">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="89950-117">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-117">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="89950-118">작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89950-118">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="89950-119">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-119">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="89950-120">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-120">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="89950-121">**형식** 목록에서 **PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-121">In the **Type** list, click **PowerShell**.</span></span>  
  
6.  <span data-ttu-id="89950-122">**다음 계정으로 실행** 목록에서 작업에 사용할 자격 증명을 가진 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-122">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="89950-123">**명령** 입력란에 작업 단계를 위해 실행될 PowerShell 스크립트 구문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-123">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="89950-124">아니면 **열기** 를 클릭한 다음 해당 스크립트 구문이 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-124">Alternately, click **Open** and select a file containing the script syntax.</span></span> <span data-ttu-id="89950-125">PowerShell 스크립트 예는 아래의 **Transact-SQL 사용** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89950-125">For an example of a PowerShell script, see **Using Transact-SQL** below.</span></span>  
  
8.  <span data-ttu-id="89950-126">**고급** 페이지를 클릭하여 작업 단계가 성공 또는 실패할 경우에 수행할 동작, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 작업 단계 실행 시도 횟수, 그리고 다시 시도 간격 등 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="89950-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="89950-127">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="89950-128">PowerShell 스크립트 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="89950-128">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="89950-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="89950-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="89950-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a PowerShell job step that finds the processes that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="89950-132">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89950-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="89950-133">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="89950-133">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="89950-134">**PowerShell 스크립트 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="89950-134">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="89950-135">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="89950-135">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
