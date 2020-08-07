---
title: 작업 중지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727887"
---
# <a name="stop-a-job"></a><span data-ttu-id="57ce9-102">Stop a Job</span><span class="sxs-lookup"><span data-stu-id="57ce9-102">Stop a Job</span></span>
  <span data-ttu-id="57ce9-103">이 항목에서는 에이전트 작업을 중지 하는 방법에 대해 설명 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-103">This topic describes how to stop a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="57ce9-104">작업은 SQL Server 에이전트에서 수행하도록 지정된 일련의 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-104">A job is a specified series of actions that SQL Server Agent performs.</span></span>  
  
-   <span data-ttu-id="57ce9-105">**시작 하기 전에:** ,</span><span class="sxs-lookup"><span data-stu-id="57ce9-105">**Before you begin:**  ,</span></span>  
  
     [<span data-ttu-id="57ce9-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="57ce9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="57ce9-107">보안</span><span class="sxs-lookup"><span data-stu-id="57ce9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="57ce9-108">**작업을 중지하려면:**</span><span class="sxs-lookup"><span data-stu-id="57ce9-108">**To stop a job, using:**</span></span>  
  
     [<span data-ttu-id="57ce9-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="57ce9-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="57ce9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="57ce9-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="57ce9-111">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="57ce9-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="57ce9-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="57ce9-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="57ce9-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="57ce9-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="57ce9-114">작업이 현재 **CmdExec** 또는 **PowerShell**유형의 단계를 실행하고 있는 경우에는 실행 중인 프로세스(예: MyProgram.exe)가 중간에 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-114">If a job is currently executing a step of type **CmdExec** or **PowerShell**, the process that is being run (for example, MyProgram.exe) is forced to end prematurely.</span></span> <span data-ttu-id="57ce9-115">이로 인해 프로세스가 보유하고 있던 파일이 열리는 등 예기치 않은 상황이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-115">This can cause unpredictable behavior, such as files that are being used by the process being held open.</span></span>  
  
-   <span data-ttu-id="57ce9-116">다중 서버 작업의 경우 해당 작업에 대한 STOP 명령이 작업의 모든 대상 서버에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-116">For a multiserver job, a STOP instruction for the job is posted to all target servers of the job.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="57ce9-117">보안</span><span class="sxs-lookup"><span data-stu-id="57ce9-117">Security</span></span>  
 <span data-ttu-id="57ce9-118">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57ce9-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="57ce9-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="57ce9-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-stop-a-job"></a><span data-ttu-id="57ce9-120">작업을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="57ce9-120">To stop a job</span></span>  
  
1.  <span data-ttu-id="57ce9-121">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-121">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="57ce9-122">**SQL Server 에이전트**, **작업**을 차례로 확장하고 중단할 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-122">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to stop, and then click **Stop Job**.</span></span>  
  
3.  <span data-ttu-id="57ce9-123">여러 작업을 중지하려면 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-123">If you want to stop multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="57ce9-124">작업 활동 모니터에서 중지하려는 작업을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-124">In the Job Activity Monitor, select the jobs you want to stop, right-click your selection, and then click **Stop Jobs**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="57ce9-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="57ce9-125">Using Transact-SQL</span></span>  
  
### <a name="to-stop-a-job"></a><span data-ttu-id="57ce9-126">작업을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="57ce9-126">To stop a job</span></span>  
  
1.  <span data-ttu-id="57ce9-127">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="57ce9-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="57ce9-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="57ce9-130">자세한 내용은 [sp_stop_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57ce9-130">For more information, see [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="57ce9-131">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="57ce9-131">Using SQL Server Management Objects</span></span>  

### <a name="to-stop-a-job"></a><span data-ttu-id="57ce9-132">작업을 중지하려면</span><span class="sxs-lookup"><span data-stu-id="57ce9-132">To stop a job</span></span>
  
 <span data-ttu-id="57ce9-133">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Stop` 클래스의 `Job` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce9-133">Call the `Stop` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="57ce9-134">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57ce9-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
