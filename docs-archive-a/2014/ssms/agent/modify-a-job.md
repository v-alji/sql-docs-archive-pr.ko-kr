---
title: 작업 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649343"
---
# <a name="modify-a-job"></a><span data-ttu-id="54429-102">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="54429-102">Modify a Job</span></span>
  <span data-ttu-id="54429-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업의 속성을 변경 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="54429-103">This topic describes how to change the properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="54429-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="54429-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="54429-105">**시작하기 전 주의 사항:** ,</span><span class="sxs-lookup"><span data-stu-id="54429-105">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="54429-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="54429-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="54429-107">보안</span><span class="sxs-lookup"><span data-stu-id="54429-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="54429-108">**작업을 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="54429-108">**To modify a job, using:**</span></span>  
  
     [<span data-ttu-id="54429-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="54429-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="54429-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="54429-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="54429-111">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="54429-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="54429-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="54429-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="54429-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="54429-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="54429-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 마스터 작업은 로컬 및 원격 서버 모두에서 대상이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54429-114">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="54429-115">보안</span><span class="sxs-lookup"><span data-stu-id="54429-115">Security</span></span>  
 <span data-ttu-id="54429-116">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54429-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="54429-117">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54429-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="54429-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="54429-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="54429-119">작업을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="54429-119">To modify a job</span></span>  
  
1.  <span data-ttu-id="54429-120">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="54429-121">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 수정할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="54429-122">**작업 속성** 대화 상자에서 해당 페이지를 사용하여 작업의 속성, 단계, 일정, 경고 및 알림을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-122">In the **Job Properties** dialog box, update the job's properties, steps, schedule, alerts, and notifications using the corresponding pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="54429-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="54429-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="54429-124">작업을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="54429-124">To modify a job</span></span>  
  
1.  <span data-ttu-id="54429-125">개체 탐색기에서 데이터베이스 엔진의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-125">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="54429-126">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-126">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="54429-127">쿼리 창에서 다음 시스템 저장 프로시저를 사용하여 작업을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-127">In the query window, use the following system stored procedures to modify a job.</span></span>  
  
    -   <span data-ttu-id="54429-128">[Transact-sql&#41;&#40;sp_update_job](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) 을 실행 하 여 작업의 특성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-128">Execute [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) to change the attributes of a job.</span></span>  
  
    -   <span data-ttu-id="54429-129">[Transact-sql&#41;&#40;sp_update_schedule](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) 을 실행 하 여 작업 정의에 대 한 일정 정보를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-129">Execute [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) to change the scheduling details for a job definition.</span></span>  
  
    -   <span data-ttu-id="54429-130">[Transact-sql&#41;&#40;sp_add_jobstep](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) 를 실행 하 여 새 작업 단계를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-130">Execute [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) to add new job steps.</span></span>  
  
    -   <span data-ttu-id="54429-131">[Transact-sql&#41;&#40;sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) 실행 하 여 기존 작업 단계를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-131">Execute [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) to change pre-existing job steps.</span></span>  
  
    -   <span data-ttu-id="54429-132">[Transact-sql&#41;&#40;sp_delete_jobstep](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) 을 실행 하 여 작업에서 작업 단계를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-132">Execute [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) to remove a job step from a job.</span></span>  
  
    -   <span data-ttu-id="54429-133">SQL Server 에이전트 마스터 작업을 수정하는 추가 저장 프로시저:</span><span class="sxs-lookup"><span data-stu-id="54429-133">Additional stored procedures to modify any SQL Server Agent master job:</span></span>  
  
        -   <span data-ttu-id="54429-134">[Transact-sql&#41;&#40;sp_delete_jobserver](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) 를 실행 하 여 현재 작업과 연결 된 서버를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-134">Execute [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) to delete a server currently associated with a job.</span></span>  
  
        -   <span data-ttu-id="54429-135">[Transact-sql&#41;&#40;sp_add_jobserver](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) 를 실행 하 여 현재 작업과 서버를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-135">Execute [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) to associate a server with the current job.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="54429-136">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="54429-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="54429-137">**작업을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="54429-137">**To modify a job**</span></span>  
  
 <span data-ttu-id="54429-138">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Job` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="54429-138">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="54429-139">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54429-139">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
