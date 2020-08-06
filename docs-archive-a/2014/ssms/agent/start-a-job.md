---
title: 작업 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737414"
---
# <a name="start-a-job"></a><span data-ttu-id="57770-102">작업 시작</span><span class="sxs-lookup"><span data-stu-id="57770-102">Start a Job</span></span>
  <span data-ttu-id="57770-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 실행을 시작 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57770-103">This topic describes how to start running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="57770-104">작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행하도록 지정된 일련의 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="57770-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="57770-105">에이전트 작업은 한 대의 로컬 서버나 다중 원격 서버에서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57770-105">Agent jobs can run on one local server or on multiple remote servers.</span></span>  
  
-   <span data-ttu-id="57770-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="57770-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="57770-107">보안</span><span class="sxs-lookup"><span data-stu-id="57770-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="57770-108">**작업을 시작하려면:**</span><span class="sxs-lookup"><span data-stu-id="57770-108">**To start a job, using:**</span></span>  
  
     [<span data-ttu-id="57770-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="57770-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="57770-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="57770-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="57770-111">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="57770-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="57770-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="57770-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="57770-113">보안</span><span class="sxs-lookup"><span data-stu-id="57770-113">Security</span></span>  
 <span data-ttu-id="57770-114">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57770-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="57770-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="57770-115">Using SQL Server Management Studio</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="57770-116">작업을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="57770-116">To start a job</span></span>  
  
1.  <span data-ttu-id="57770-117">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="57770-118">**SQL Server 에이전트** 를 확장한 다음 **작업**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-118">Expand **SQL Server Agent,** and expand **Jobs**.</span></span> <span data-ttu-id="57770-119">원하는 작업 시작 방법에 따라 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-119">Depending on how you want the job to start, do one of the following:</span></span>  
  
    -   <span data-ttu-id="57770-120">단일 서버 또는 대상 서버에서 작업 중이거나 마스터 서버에서 로컬 서버 작업을 실행하고 있는 경우 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-120">If you are working on a single server, or working on a target server, or running a local server job on a master server, right-click the job you want to start, and then click **Start Job**.</span></span>  
  
    -   <span data-ttu-id="57770-121">여러 작업을 시작하려면 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-121">If you want to start multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="57770-122">작업 활동 모니터에서 여러 작업을 선택한 다음 마우스 오른쪽 단추로 클릭하고 **작업 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-122">In the Job Activity Monitor you can select multiple jobs, right-click your selection, and click **Start Jobs**.</span></span>  
  
    -   <span data-ttu-id="57770-123">마스터 서버에서 작업 중이고 모든 대상 서버에서 동시에 작업을 실행하려는 경우에는 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**, **모든 대상 서버에서 시작**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-123">If you are working on a master server and want all targeted servers to run the job simultaneously, right-click the job you want to start, click **Start Job**, and then click **Start on all targeted servers**.</span></span>  
  
    -   <span data-ttu-id="57770-124">마스터 서버에서 작업 중이고 작업 대상 서버를 지정하려는 경우에는 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**, **특정 대상 서버에서 시작**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-124">If you are working on a master server and want to specify target servers for the job, right-click the job you want to start, click **Start Job**, and then click **Start on specific target servers**.</span></span> <span data-ttu-id="57770-125">**다운로드 명령 게시** 대화 상자에서 **대상 서버 지정** 확인란을 선택한 다음 작업을 실행할 각각의 대상 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-125">In the **Post Download Instructions** dialog box, select the **These target servers** check box, and then select each target server on which this job should run.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="57770-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="57770-126">Using Transact-SQL</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="57770-127">작업을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="57770-127">To start a job</span></span>  
  
1.  <span data-ttu-id="57770-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="57770-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="57770-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="57770-131">자세한 내용은 [sp_start_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57770-131">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="57770-132">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="57770-132">Using SQL Server Management Objects</span></span>  

### <a name="to-start-a-job"></a><span data-ttu-id="57770-133">작업을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="57770-133">To start a job</span></span>
  
 <span data-ttu-id="57770-134">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Start` 클래스의 `Job` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="57770-134">Call the `Start` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="57770-135">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57770-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
