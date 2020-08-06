---
title: SQL Server 에이전트 마스터 작업과 연결 된 대상 서버 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b7b5ab114366cdafe40b7a70f523fef43eb11d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660836"
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="d20ce-102">SQL Server 에이전트 마스터 작업과 연관된 대상 서버 수정</span><span class="sxs-lookup"><span data-stu-id="d20ce-102">Modify the Target Server(s) Associated with a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="d20ce-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 SQL Server 에이전트 마스터 작업과 연결된 대상 서버를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-103">This topic describes how to modify the target server(s) associated with a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d20ce-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d20ce-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d20ce-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d20ce-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d20ce-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d20ce-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d20ce-107">보안</span><span class="sxs-lookup"><span data-stu-id="d20ce-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d20ce-108">**다음을 사용하여 SQL Server 에이전트 마스터 작업과 연결된 대상 서버를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="d20ce-108">**To modify the target server(s) associated with a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="d20ce-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d20ce-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d20ce-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d20ce-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d20ce-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d20ce-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d20ce-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d20ce-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d20ce-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 마스터 작업은 로컬 및 원격 서버 모두에서 대상이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d20ce-114">보안</span><span class="sxs-lookup"><span data-stu-id="d20ce-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d20ce-115">권한</span><span class="sxs-lookup"><span data-stu-id="d20ce-115">Permissions</span></span>  
 <span data-ttu-id="d20ce-116">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="d20ce-117">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d20ce-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d20ce-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d20ce-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="d20ce-119">SQL Server 에이전트 마스터 작업과 연결된 대상 서버를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="d20ce-119">To modify the target server(s) associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="d20ce-120">**개체 탐색기** 에서 더하기 기호를 클릭하여 대상 서버를 수정할 작업이 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify the target server.</span></span>  
  
2.  <span data-ttu-id="d20ce-121">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d20ce-122">더하기 기호를 클릭하여 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="d20ce-123">대상 서버를 수정할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-123">Right-click the job where you want to modify the target server and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="d20ce-124">**작업 속성-**_job_name_ 대화 상자의 **페이지 선택**에서 **대상**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Targets**.</span></span> <span data-ttu-id="d20ce-125">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;대상 페이지&#41;](job-properties-new-job-targets-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d20ce-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
6.  <span data-ttu-id="d20ce-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d20ce-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d20ce-127">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="d20ce-128">현재 SQL Server 에이전트 마스터 작업과 연결되어 있는 대상 서버를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="d20ce-128">To delete a target server currently associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="d20ce-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d20ce-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d20ce-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="d20ce-132">자세한 내용은 [sp_delete_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d20ce-132">For more information, see [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql).</span></span>  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a><span data-ttu-id="d20ce-133">대상 서버를 현재 SQL Server 에이전트 마스터 작업과 연결하려면</span><span class="sxs-lookup"><span data-stu-id="d20ce-133">To associate a target server with the current SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="d20ce-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d20ce-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d20ce-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d20ce-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="d20ce-137">자세한 내용은 [sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d20ce-137">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
  
