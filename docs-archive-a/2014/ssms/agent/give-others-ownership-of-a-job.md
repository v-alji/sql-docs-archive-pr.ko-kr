---
title: 작업의 소유권을 다른 사용자에게 제공 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2cf03fdc9031ce9761125d95619438837f2959bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639218"
---
# <a name="give-others-ownership-of-a-job"></a><span data-ttu-id="82ae9-102">Give Others Ownership of a Job</span><span class="sxs-lookup"><span data-stu-id="82ae9-102">Give Others Ownership of a Job</span></span>
  <span data-ttu-id="82ae9-103">이 항목에서는 에이전트 작업의 소유권을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 다른 사용자에 게 다시 할당 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-103">This topic describes how to reassign ownership of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>  
  
-   <span data-ttu-id="82ae9-104">**시작하기 전 주의 사항:**  [제한 사항](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="82ae9-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="82ae9-105">**작업의 소유권을 다른 사용자에게 제공하려면:**</span><span class="sxs-lookup"><span data-stu-id="82ae9-105">**To give others ownership of a job, using:**</span></span>  
  
     [<span data-ttu-id="82ae9-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="82ae9-106">SQL Server Management Studio</span></span>](#SSMSProc2)  
  
     [<span data-ttu-id="82ae9-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="82ae9-107">Transact-SQL</span></span>](#TsqlProc2)  
  
     [<span data-ttu-id="82ae9-108">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="82ae9-108">SQL Server Management Objects</span></span>](#SMOProc2)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="82ae9-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="82ae9-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="82ae9-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="82ae9-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="82ae9-111">작업을 만들려면 사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할이나 **sysadmin** 고정 서버 역할 중 하나의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-111">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="82ae9-112">작업은 소유자나 **sysadmin** 역할의 멤버만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-112">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="82ae9-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82ae9-113">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="82ae9-114">작업 소유자를 변경하려면 시스템 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-114">You must be a system administrator to change the owner of a job.</span></span>  
  
 <span data-ttu-id="82ae9-115">다른 로그인에 작업을 할당한다고 해서 새 소유자가 작업을 성공적으로 실행할 수 있는 충분한 권한을 가진다고 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-115">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="82ae9-116">보안</span><span class="sxs-lookup"><span data-stu-id="82ae9-116">Security</span></span>  
 <span data-ttu-id="82ae9-117">보안을 위해 작업 소유자나 **sysadmin** 역할의 멤버만 작업 정의를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-117">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="82ae9-118">**sysadmin** 고정 서버 역할의 멤버만 작업 소유권을 다른 사용자에게 할당할 수 있으며 작업 소유자가 아니어도 모든 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-118">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82ae9-119">**sysadmin** 고정 서버 역할의 멤버가 아닌 사용자로 작업 소유권을 변경하고 이 작업이 프록시 계정을 필요로 하는 작업 단계를 실행 중이면(예: [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 실행) 사용자가 해당 프록시 계정에 액세스할 수 있어야 작업이 실패하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-119">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="82ae9-120">권한</span><span class="sxs-lookup"><span data-stu-id="82ae9-120">Permissions</span></span>  
 <span data-ttu-id="82ae9-121">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82ae9-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a> <span data-ttu-id="82ae9-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="82ae9-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="82ae9-123">**작업의 소유권을 다른 사람에게 주려면**</span><span class="sxs-lookup"><span data-stu-id="82ae9-123">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="82ae9-124">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="82ae9-125">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="82ae9-126">**소유자** 목록에서 로그인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-126">In the **Owner** list, select a login.</span></span> <span data-ttu-id="82ae9-127">작업 소유자를 변경하려면 시스템 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-127">You must be a system administrator to change the owner of a job.</span></span>  
  
     <span data-ttu-id="82ae9-128">다른 로그인에 작업을 할당한다고 해서 새 소유자가 작업을 성공적으로 실행할 수 있는 충분한 권한을 가진다고 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-128">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProc2"></a> <span data-ttu-id="82ae9-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="82ae9-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="82ae9-130">**작업의 소유권을 다른 사람에게 주려면**</span><span class="sxs-lookup"><span data-stu-id="82ae9-130">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="82ae9-131">개체 탐색기에서 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-131">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="82ae9-132">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-132">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="82ae9-133">쿼리 창에서 [sp_manage_jobs_by_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) 시스템 저장 프로시저를 사용 하는 다음 문을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-133">In the query window, enter the following statements that use the [sp_manage_jobs_by_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) system stored procedure.</span></span> <span data-ttu-id="82ae9-134">다음 예에서는 `danw` 의 모든 작업을 `fran??oisa`에 다시 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-134">The following example reassigns all jobs from `danw` to `fran??oisa`.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a><span data-ttu-id="82ae9-135">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="82ae9-135">Using SQL Server Management Objects</span></span>  

### <a name="to-give-others-ownership-of-a-job"></a><span data-ttu-id="82ae9-136">작업의 소유권을 다른 사람에게 주려면</span><span class="sxs-lookup"><span data-stu-id="82ae9-136">To give others ownership of a job</span></span>
  
1.  <span data-ttu-id="82ae9-137">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Job` 클래스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="82ae9-137">Call the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="82ae9-138">예제 코드를 보려면 [SQL Server 에이전트에서 자동 관리 태스크 예약](sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82ae9-138">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ae9-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82ae9-139">See Also</span></span>  
 <span data-ttu-id="82ae9-140">[작업 구현](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="82ae9-140">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="82ae9-141">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="82ae9-141">Create Jobs</span></span>](create-jobs.md)  
