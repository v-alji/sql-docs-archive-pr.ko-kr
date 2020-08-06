---
title: 작업 기록 로그 지우기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813c2c7c86a769eea09a093f2de999460d78ef54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660847"
---
# <a name="clear-the-job-history-log"></a><span data-ttu-id="23af8-102">Clear the Job History Log</span><span class="sxs-lookup"><span data-stu-id="23af8-102">Clear the Job History Log</span></span>
  <span data-ttu-id="23af8-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 기록 로그의 내용을 삭제 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="23af8-103">This topic describes how to delete the contents of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="23af8-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="23af8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="23af8-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="23af8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="23af8-106">보안</span><span class="sxs-lookup"><span data-stu-id="23af8-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="23af8-107">**다음을 사용하여 작업 기록 로그를 지웁니다.**</span><span class="sxs-lookup"><span data-stu-id="23af8-107">**To clear the job history log, using:**</span></span>  
  
     [<span data-ttu-id="23af8-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="23af8-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="23af8-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23af8-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="23af8-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="23af8-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="23af8-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="23af8-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="23af8-112">보안</span><span class="sxs-lookup"><span data-stu-id="23af8-112">Security</span></span>  
 <span data-ttu-id="23af8-113">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23af8-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="23af8-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="23af8-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="23af8-115">작업 기록 로그를 지우려면</span><span class="sxs-lookup"><span data-stu-id="23af8-115">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="23af8-116">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="23af8-117">**SQL Server 에이전트**를 확장한 다음 **작업**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-117">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="23af8-118">작업을 마우스 오른쪽 단추로 클릭한 다음 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-118">Right-click a job and click **View history**.</span></span>  
  
4.  <span data-ttu-id="23af8-119">**로그 파일 뷰어**에서 기록을 삭제할 작업을 선택한 후 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-119">In the **Log File Viewer**, select the job for which you want to clear history, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="23af8-120">**삭제**를 클릭한 다음 **기록 삭제** 대화 상자에서 **모든 기록 삭제** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-120">Click **Delete**, and then click **Delete all history** in the **Delete History** dialog.</span></span> <span data-ttu-id="23af8-121">모든 작업 기록 또는 지정된 날짜 이전의 기록만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-121">You can delete all job history or only history that is older than a specified date.</span></span> <span data-ttu-id="23af8-122">모든 작업 기록을 제거하려면 **모든 기록 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-122">If you want to remove all job history, click **Delete all history**.</span></span> <span data-ttu-id="23af8-123">이전 작업 기록 로그만 제거하려면 **다음 날짜 이전의 기록 삭제**를 클릭한 다음 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-123">If you only want to remove older job history logs, click **Delete history before**, and then specify a date.</span></span>  
  
    -   <span data-ttu-id="23af8-124">다중 서버 작업의 기록 로그를 지우려면 **작업 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-124">Click **Job status** if you want to clear the history log of a multiserver job.</span></span> <span data-ttu-id="23af8-125">**작업**, 작업 이름, **원격 작업 기록 보기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-125">Click **Job**, click a job name, and then click **View Remote Job History**.</span></span>  
  
5.  <span data-ttu-id="23af8-126">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-126">Click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="23af8-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="23af8-127">Using Transact-SQL</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="23af8-128">작업 기록 로그를 지우려면</span><span class="sxs-lookup"><span data-stu-id="23af8-128">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="23af8-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="23af8-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="23af8-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="23af8-132">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="23af8-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="23af8-133">**작업 기록 로그를 지우려면**</span><span class="sxs-lookup"><span data-stu-id="23af8-133">**To clear the job history log**</span></span>  
  
 <span data-ttu-id="23af8-134">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `PurgeJobHistory` 클래스의 `JobServer` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23af8-134">Use the `PurgeJobHistory` method of the `JobServer` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="23af8-135">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23af8-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
