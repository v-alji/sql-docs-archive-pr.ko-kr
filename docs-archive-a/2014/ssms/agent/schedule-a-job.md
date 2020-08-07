---
title: 작업 예약 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731324"
---
# <a name="schedule-a-job"></a><span data-ttu-id="222bf-102">Schedule a Job</span><span class="sxs-lookup"><span data-stu-id="222bf-102">Schedule a Job</span></span>
  <span data-ttu-id="222bf-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 예약하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-103">This topic describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
-   <span data-ttu-id="222bf-104">**시작하기 전 주의 사항:** ,</span><span class="sxs-lookup"><span data-stu-id="222bf-104">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="222bf-105">보안</span><span class="sxs-lookup"><span data-stu-id="222bf-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="222bf-106">**작업 일정을 예약하려면:**</span><span class="sxs-lookup"><span data-stu-id="222bf-106">**To schedule a job, using:**</span></span>  
  
     [<span data-ttu-id="222bf-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="222bf-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="222bf-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="222bf-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="222bf-109">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="222bf-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="222bf-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="222bf-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="222bf-111">보안</span><span class="sxs-lookup"><span data-stu-id="222bf-111">Security</span></span>  
 <span data-ttu-id="222bf-112">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="222bf-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="222bf-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="222bf-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a><span data-ttu-id="222bf-114">작업에 대한 일정을 만들고 연결하려면</span><span class="sxs-lookup"><span data-stu-id="222bf-114">To create and attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="222bf-115">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="222bf-116">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 예약할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-116">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="222bf-117">**일정** 페이지를 선택한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-117">Select the **Schedules** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="222bf-118">**이름** 입력란에 새 일정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="222bf-119">만든 즉시 일정이 적용되지 않게 하려면 **사용** 확인란의 선택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-119">Clear the **Enabled** check box if you do not want the schedule to take effect immediately following its creation.</span></span>  
  
6.  <span data-ttu-id="222bf-120">**일정 유형**에 대해 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="222bf-121">**SQL Server 에이전트가 시작될 때 자동으로 시작** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 시작할 때 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-121">Click **Start automatically when SQL Server Agent starts** to start the job when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is started.</span></span>  
  
    -   <span data-ttu-id="222bf-122">**CPU가 유휴 상태로 될 때마다 시작** 을 클릭하여 CPU가 유휴 상태일 때 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-122">Click **Start whenever the CPUs become idle** to start the job when the CPUs reach an idle condition.</span></span>  
  
    -   <span data-ttu-id="222bf-123">일정을 반복적으로 실행하려면 **되풀이** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-123">Click **Recurring** if you want a schedule to run repeatedly.</span></span> <span data-ttu-id="222bf-124">반복 수행 일정을 설정하려면 대화 상자에서 **빈도**, **일별 빈도**및 **기간** 그룹을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="222bf-124">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="222bf-125">한 번만 실행하도록 예약하려면 **한 번** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-125">Click **One time** if you want the schedule to run only once.</span></span> <span data-ttu-id="222bf-126">**한 번** 예약을 설정하려면 대화 상자에서 **한 번 발생** 그룹을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-126">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog.</span></span>  
  
#### <a name="to-attach-a-schedule-to-a-job"></a><span data-ttu-id="222bf-127">작업에 일정을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="222bf-127">To attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="222bf-128">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-128">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="222bf-129">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 예약할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-129">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="222bf-130">**일정** 페이지를 선택한 다음 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-130">Select the **Schedules** page, and then click **Pick**.</span></span>  
  
4.  <span data-ttu-id="222bf-131">연결하려는 일정을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-131">Select the schedule that you want to attach, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="222bf-132">**작업 속성** 대화 상자에서 연결된 일정을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-132">In the **Job Properties** dialog box, double-click the attached schedule.</span></span>  
  
6.  <span data-ttu-id="222bf-133">**시작 날짜** 가 올바르게 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-133">Verify that **Start date** is set correctly.</span></span> <span data-ttu-id="222bf-134">올바르게 설정되지 않았으면 일정을 시작하려는 날짜를 설정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-134">If it is not, set the date when you want for the schedule to start, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="222bf-135">**작업 속성** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-135">In the **Job Properties** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="222bf-136">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="222bf-136">Using Transact-SQL</span></span>  
  
#### <a name="to-schedule-a-job"></a><span data-ttu-id="222bf-137">작업을 예약하려면</span><span class="sxs-lookup"><span data-stu-id="222bf-137">To schedule a job</span></span>  
  
1.  <span data-ttu-id="222bf-138">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="222bf-139">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="222bf-140">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="222bf-141">자세한 내용은 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) 및 [sp_attach_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="222bf-141">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) and [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="222bf-142">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="222bf-142">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="222bf-143">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobSchedule` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="222bf-143">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="222bf-144">자세한 내용은[SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="222bf-144">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
