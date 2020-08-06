---
title: SQL Server 에이전트 마스터 작업에 단계 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9cc1e8ab-7ddc-427b-859e-203aa7e24642
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccff8d6f4faa7bef549b5a179a957ce798250dbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638533"
---
# <a name="add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="0d162-102">Add Steps to a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="0d162-102">Add Steps to a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="0d162-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 SQL Server 에이전트 마스터 작업에 단계를 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-103">This topic describes how to add steps to a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0d162-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0d162-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d162-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0d162-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d162-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0d162-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0d162-107">보안</span><span class="sxs-lookup"><span data-stu-id="0d162-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d162-108">**다음을 사용하여 SQL Server 에이전트 마스터 작업에 단계를 추가하려면:**</span><span class="sxs-lookup"><span data-stu-id="0d162-108">**To add steps to a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="0d162-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d162-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0d162-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d162-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d162-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0d162-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0d162-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0d162-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0d162-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 마스터 작업은 로컬 및 원격 서버 모두에서 대상이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d162-114">보안</span><span class="sxs-lookup"><span data-stu-id="0d162-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d162-115">권한</span><span class="sxs-lookup"><span data-stu-id="0d162-115">Permissions</span></span>  
 <span data-ttu-id="0d162-116">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="0d162-117">자세한 내용은 [SQL Server 에이전트 보안 구현](../agent/implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d162-117">For detailed information, see [Implement SQL Server Agent Security](../agent/implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d162-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0d162-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="0d162-119">SQL Server 에이전트 마스터 작업에 단계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0d162-119">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="0d162-120">**개체 탐색기** 에서 더하기 기호를 클릭하여 단계를 추가하려는 작업이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-120">In **Object Explorer,** click the plus sign to expand the server that contains the job to which you want to add steps.</span></span>  
  
2.  <span data-ttu-id="0d162-121">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="0d162-122">더하기 기호를 클릭하여 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="0d162-123">단계를 추가하려는 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-123">Right-click the job to which you want to add steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="0d162-124">**Job Properties -** _job_name_ 대화 상자의 **페이지 선택**에서 **단계**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span> <span data-ttu-id="0d162-125">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;단계 페이지&#41;](../agent/job-properties-new-job-steps-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d162-125">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](../agent/job-properties-new-job-steps-page.md).</span></span>  

6.  <span data-ttu-id="0d162-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0d162-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0d162-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="0d162-128">SQL Server 에이전트 마스터 작업에 단계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0d162-128">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="0d162-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d162-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d162-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d162-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a job step that changes database access to read-only for the Sales database.   
    -- specifies 5 retry attempts, with each retry to occur after a 5 minute wait.   
    -- assumes that the Weekly Sales Data Backup job already exists  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="0d162-132">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d162-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
  
