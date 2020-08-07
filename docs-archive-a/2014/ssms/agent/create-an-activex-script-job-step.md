---
title: ActiveX 스크립트 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6604ba75af7acdd5bd2521433e8310c74150ce8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727903"
---
# <a name="create-an-activex-script-job-step"></a><span data-ttu-id="f1020-102">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="f1020-102">Create an ActiveX Script Job Step</span></span>
  <span data-ttu-id="f1020-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 ActiveX 스크립트를 실행 하는 에이전트 작업 단계를 만들고 정의 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f1020-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that executes an ActiveX script by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="f1020-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f1020-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f1020-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f1020-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f1020-106">보안</span><span class="sxs-lookup"><span data-stu-id="f1020-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f1020-107">**Transact-SQL 작업 단계를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="f1020-107">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="f1020-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f1020-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="f1020-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f1020-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="f1020-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="f1020-110">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="f1020-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f1020-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f1020-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f1020-112">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f1020-113">보안</span><span class="sxs-lookup"><span data-stu-id="f1020-113">Security</span></span>  
 <span data-ttu-id="f1020-114">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1020-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="f1020-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f1020-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="f1020-116">ActiveX 스크립트 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f1020-116">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="f1020-117">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f1020-118">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="f1020-119">작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1020-119">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="f1020-120">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="f1020-121">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="f1020-122">**유형** 목록에서 **ActiveX 스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-122">In the **Type** list, click **ActiveX Script**.</span></span>  
  
6.  <span data-ttu-id="f1020-123">**다음 계정으로 실행** 목록에서 작업에 사용할 자격 증명을 가진 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="f1020-124">스크립트 작성에 사용한 **언어** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-124">Select the **Language** in which the script was written.</span></span> <span data-ttu-id="f1020-125">또는 **기타** 를 클릭한 다음 스크립트 작성에 사용할 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX 스크립트 언어의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-125">Alternatively, click **Other** and then enter the name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX scripting language in which the script will be written.</span></span>  
  
8.  <span data-ttu-id="f1020-126">**명령** 입력란에 작업 단계를 위해 실행될 스크립트 구문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-126">In the **Command** box, enter the script syntax that will be executed for the job step.</span></span> <span data-ttu-id="f1020-127">아니면 **열기** 를 클릭한 다음 해당 스크립트 구문이 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-127">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
9. <span data-ttu-id="f1020-128">**고급** 페이지를 클릭하여 작업 단계가 성공 또는 실패할 경우에 수행할 동작, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 작업 단계 실행 시도 횟수, 그리고 다시 시도 간격 등 작업 단계 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-128">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="f1020-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f1020-129">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="f1020-130">ActiveX 스크립트 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f1020-130">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="f1020-131">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f1020-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f1020-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="f1020-134">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1020-134">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="f1020-135">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="f1020-135">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="f1020-136">**ActiveX 스크립트 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="f1020-136">**To create an ActiveX Script job step**</span></span>  
  
 <span data-ttu-id="f1020-137">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1020-137">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
