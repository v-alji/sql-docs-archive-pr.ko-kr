---
title: 일정 만들기 | Microsoft 문서
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
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659788"
---
# <a name="create-a-schedule"></a><span data-ttu-id="25211-102">Create a Schedule</span><span class="sxs-lookup"><span data-stu-id="25211-102">Create a Schedule</span></span>
  <span data-ttu-id="25211-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 SQL Server 관리 개체를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 작업에 대한 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25211-103">You can create a schedule for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="25211-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="25211-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="25211-105">보안</span><span class="sxs-lookup"><span data-stu-id="25211-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="25211-106">**일정을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="25211-106">**To create a schedule, using:**</span></span>  
  
     [<span data-ttu-id="25211-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25211-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="25211-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25211-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="25211-109">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="25211-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="25211-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="25211-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="25211-111">보안</span><span class="sxs-lookup"><span data-stu-id="25211-111">Security</span></span>  
 <span data-ttu-id="25211-112">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25211-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="25211-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="25211-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="25211-114">일정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="25211-114">To create a schedule</span></span>  
  
1.  <span data-ttu-id="25211-115">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="25211-116">**SQL Server 에이전트**를 확장하고 **작업**을 마우스 오른쪽 단추로 클릭한 후 **일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-116">Expand **SQL Server Agent**, right-click **Jobs**, and select **Manage Schedules**.</span></span>  
  
3.  <span data-ttu-id="25211-117">**일정 관리** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-117">In the **Manage Schedules** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="25211-118">**이름** 입력란에 새 일정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="25211-119">만든 즉시 일정이 적용되지 않게 하려면 **사용** 확인란의 선택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-119">If you do not want the schedule to take effect immediately after it has been created, clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="25211-120">**일정 유형**에 대해 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="25211-121">CPU가 유휴 상태일 때 작업을 시작하려면 **CPU가 유휴 상태로 될 때마다 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-121">To start the job when the CPUs reach an idle condition, click **Start whenever the CPUs become idle**.</span></span>  
  
    -   <span data-ttu-id="25211-122">일정을 반복적으로 실행하려면 **되풀이**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-122">If you want a schedule to run repeatedly, click **Recurring**.</span></span> <span data-ttu-id="25211-123">반복 수행 일정을 설정하려면 대화 상자에서 **빈도**, **일별 빈도**및 **기간** 그룹을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="25211-123">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="25211-124">한 번만 실행하도록 예약하려면 **한 번**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-124">If you want the schedule to run only one time, click **One time**.</span></span> <span data-ttu-id="25211-125">**한 번** 예약을 설정하려면 대화 상자에서 **한 번 발생** 그룹을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-125">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="25211-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="25211-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="25211-127">일정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="25211-127">To create a schedule</span></span>  
  
1.  <span data-ttu-id="25211-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25211-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25211-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 <span data-ttu-id="25211-131">자세한 내용은 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25211-131">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="25211-132">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="25211-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="25211-133">**일정을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="25211-133">**To create a schedule**</span></span>  
  
 <span data-ttu-id="25211-134">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobSchedule` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25211-134">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="25211-135">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25211-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
