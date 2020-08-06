---
title: 작업 기록 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
ms.openlocfilehash: e84fafdaeddb5748a8129cd5d71d667db7e5fa37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734892"
---
# <a name="view-the-job-history"></a><span data-ttu-id="a39f6-102">View the Job History</span><span class="sxs-lookup"><span data-stu-id="a39f6-102">View the Job History</span></span>
  <span data-ttu-id="a39f6-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 기록 로그를 보는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a39f6-103">This topic describes how to view the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="a39f6-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a39f6-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a39f6-105">보안</span><span class="sxs-lookup"><span data-stu-id="a39f6-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a39f6-106">**작업 기록 로그를 보려면:**</span><span class="sxs-lookup"><span data-stu-id="a39f6-106">**To view the job history log, using:**</span></span>  
  
     [<span data-ttu-id="a39f6-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a39f6-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="a39f6-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a39f6-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="a39f6-109">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="a39f6-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a39f6-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a39f6-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a39f6-111">보안</span><span class="sxs-lookup"><span data-stu-id="a39f6-111">Security</span></span>  
 <span data-ttu-id="a39f6-112">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f6-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="a39f6-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a39f6-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="a39f6-114">작업 기록 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="a39f6-114">To view the job history log</span></span>  
  
1.  <span data-ttu-id="a39f6-115">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a39f6-116">**SQL Server 에이전트**를 확장한 다음 **작업**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-116">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="a39f6-117">작업을 마우스 오른쪽 단추로 클릭한 다음 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-117">Right-click a job, and then click **View History**.</span></span>  
  
4.  <span data-ttu-id="a39f6-118">로그 파일 뷰어에서 작업 기록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-118">In the Log File Viewer, view the job history.</span></span>  
  
5.  <span data-ttu-id="a39f6-119">작업 기록을 업데이트하려면 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-119">To update the job history, click **Refresh**.</span></span> <span data-ttu-id="a39f6-120">행을 적게 표시하려면 **필터** 단추를 클릭하고 필터 매개 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-120">To view fewer rows, click the **Filter** button and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="a39f6-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a39f6-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="a39f6-122">작업 기록 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="a39f6-122">To view the job history log</span></span>  
  
1.  <span data-ttu-id="a39f6-123">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a39f6-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a39f6-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="a39f6-126">자세한 내용은 [sp_help_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f6-126">For more information, see [sp_help_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="a39f6-127">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="a39f6-127">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="a39f6-128">**작업 기록 로그를 보려면**</span><span class="sxs-lookup"><span data-stu-id="a39f6-128">**To view the job history log**</span></span>  
  
 <span data-ttu-id="a39f6-129">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `EnumHistory` 클래스의 `Job` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f6-129">Call the `EnumHistory` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="a39f6-130">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f6-130">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
