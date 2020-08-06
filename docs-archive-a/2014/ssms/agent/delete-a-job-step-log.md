---
title: 작업 단계 로그 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
ms.openlocfilehash: de7c64c4d7cf461eef563ae6989e043d125c6f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651993"
---
# <a name="delete-a-job-step-log"></a><span data-ttu-id="4dce3-102">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="4dce3-102">Delete a Job Step Log</span></span>
  <span data-ttu-id="4dce3-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계 로그를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>  
  
-   <span data-ttu-id="4dce3-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4dce3-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4dce3-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4dce3-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4dce3-106">보안</span><span class="sxs-lookup"><span data-stu-id="4dce3-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4dce3-107">**SQL Server 에이전트 작업 단계 로그를 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="4dce3-107">**To delete a SQL Server Agent job step log, using:**</span></span>  
  
     [<span data-ttu-id="4dce3-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4dce3-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="4dce3-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4dce3-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="4dce3-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="4dce3-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4dce3-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4dce3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4dce3-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4dce3-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4dce3-113">작업 단계를 삭제하면 해당 출력 로그가 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-113">When job steps are deleted their output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4dce3-114">보안</span><span class="sxs-lookup"><span data-stu-id="4dce3-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4dce3-115">권한</span><span class="sxs-lookup"><span data-stu-id="4dce3-115">Permissions</span></span>  
 <span data-ttu-id="4dce3-116">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="4dce3-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4dce3-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="4dce3-118">SQL Server 에이전트 작업 단계 로그를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4dce3-118">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="4dce3-119">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4dce3-120">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 수정할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-120">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4dce3-121">**작업 속성** 대화 상자에서 선택한 작업 단계를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-121">In the **Job Properties** dialog box, delete the selected job step.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="4dce3-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4dce3-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="4dce3-123">SQL Server 에이전트 작업 단계 로그를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4dce3-123">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="4dce3-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4dce3-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4dce3-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 <span data-ttu-id="4dce3-127">자세한 내용은 [sp_delete_jobsteplog &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4dce3-127">For more information, see [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="4dce3-128">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="4dce3-128">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="4dce3-129">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `DeleteJobStepLogs` 클래스의 `Job` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4dce3-129">Use the `DeleteJobStepLogs` methods of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="4dce3-130">자세한 내용은[SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4dce3-130">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
