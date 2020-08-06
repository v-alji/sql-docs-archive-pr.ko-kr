---
title: 작업 단계 성공 또는 실패 흐름 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: fddc5820676cb231b6f0cd5f7151e24d8eceaefa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742735"
---
# <a name="set-job-step-success-or-failure-flow"></a><span data-ttu-id="3a410-102">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="3a410-102">Set Job Step Success or Failure Flow</span></span>
  <span data-ttu-id="3a410-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 만들 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업 실행 중에 오류가 발생 하는 경우 수행할 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-103">When creating [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you can specify what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span> <span data-ttu-id="3a410-104">각 작업 단계의 성공이나 실패에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 수행해야 할 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-104">Determine the action that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take upon the success or failure of each job step.</span></span> <span data-ttu-id="3a410-105">그런 후에 다음 프로시저를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 통해 작업 단계 동작 흐름 논리를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-105">Then use the following procedure to configure the job step action flow logic by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="3a410-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3a410-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3a410-107">보안</span><span class="sxs-lookup"><span data-stu-id="3a410-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3a410-108">**작업 단계 성공 또는 실패 흐름을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="3a410-108">**To set job step success or failure flow, using:**</span></span>  
  
     [<span data-ttu-id="3a410-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3a410-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="3a410-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3a410-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="3a410-111">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="3a410-111">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="3a410-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3a410-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3a410-113">보안</span><span class="sxs-lookup"><span data-stu-id="3a410-113">Security</span></span>  
 <span data-ttu-id="3a410-114">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a410-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="3a410-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3a410-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="3a410-116">작업 단계 성공 또는 실패 흐름을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3a410-116">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="3a410-117">**개체 탐색기**에서 **SQL Server 에이전트**, **작업**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-117">In **Object Explorer**, expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
2.  <span data-ttu-id="3a410-118">편집할 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-118">Right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3a410-119">**단계** 페이지를 선택하고 단계를 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-119">Select the **Steps** page, click a step, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="3a410-120">**작업 단계 속성** 대화 상자에서 **고급** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-120">In the **Job Step Properties** dialog box, select the **Advanced** page.</span></span>  
  
5.  <span data-ttu-id="3a410-121">실패한 것으로 간주될 때까지 작업 단계를 반복할 횟수를 0부터 9999 범위에서 **성공한 경우 동작**목록에서 작업 단계가 성공적으로 완료된 경우 수행할 동작을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-121">In the **On success action**list, click the action to perform if the job step completes successfully.</span></span>  
  
6.  <span data-ttu-id="3a410-122">실패한 것으로 간주될 때까지 작업 단계를 반복할 횟수를 0부터 9999 범위에서 **다시 시도 횟수** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-122">In the **Retry attempts** box, enter the number of times from 0 through 9999 that the job step should be repeated before it is considered to have failed.</span></span> <span data-ttu-id="3a410-123">**다시 시도 횟수** 상자에 0보다 큰 값을 입력한 경우 작업 단계를 다시 시도하기 전에 경과해야 하는 시간(분)을 1부터 9999 범위에서 **다시 시도 간격(분)** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-123">If you entered a value greater than 0 in the **Retry attempts** box, enter in the **Retry interval (minutes)** box the number of minutes from 1 through 9999 that must pass before the job step is retried.</span></span>  
  
7.  <span data-ttu-id="3a410-124">**실패한 경우 동작** 목록에서 작업 단계가 실패한 경우 수행할 동작을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-124">In the **On failure action** list, click the action to perform if the job step fails.</span></span>  
  
8.  <span data-ttu-id="3a410-125">작업이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트인 경우 다음 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-125">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="3a410-126">**출력 파일** 상자에 스크립트 출력을 작성할 출력 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-126">In the **Output file** box, enter the name of an output file to which the script output will be written.</span></span> <span data-ttu-id="3a410-127">기본적으로 작업 단계가 실행될 때마다 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-127">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="3a410-128">출력 파일을 덮어쓰지 않으려면 **기존 파일에 출력 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-128">If you do not want the output file overwritten, check **Append output to existing file**.</span></span>  
  
    -   <span data-ttu-id="3a410-129">작업 단계를 데이터베이스 테이블에 기록하려면 **테이블에 기록** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-129">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="3a410-130">기본적으로 작업 단계가 실행될 때마다 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-130">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="3a410-131">테이블 내용을 덮어쓰지 않으려면 **테이블의 기존 항목에 출력 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-131">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="3a410-132">작업 단계가 실행된 다음에는 **뷰**를 클릭하여 이 테이블의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-132">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="3a410-133">출력을 단계 기록에 포함하려면 **기록에 단계 출력 포함** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-133">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="3a410-134">출력은 오류가 없을 때만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-134">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="3a410-135">또한 출력이 잘릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-135">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="3a410-136">**다음 사용자 이름으로 실행** 목록을 사용할 수 있으면 작업에서 사용할 자격 증명이 있는 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-136">If the **Run as user** list is available, select the proxy account with the credentials that the job will use.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="3a410-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3a410-137">Using Transact-SQL</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="3a410-138">작업 단계 성공 또는 실패 흐름을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3a410-138">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="3a410-139">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a410-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3a410-141">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
 <span data-ttu-id="3a410-142">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a410-142">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="3a410-143">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="3a410-143">Using SQL Server Management Objects</span></span>  

### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="3a410-144">작업 단계 성공 또는 실패 흐름을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3a410-144">To set job step success or failure flow</span></span>
  
 <span data-ttu-id="3a410-145">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a410-145">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="3a410-146">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a410-146">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
