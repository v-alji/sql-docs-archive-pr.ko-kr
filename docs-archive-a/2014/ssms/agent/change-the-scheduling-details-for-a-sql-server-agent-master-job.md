---
title: SQL Server 에이전트 마스터 작업에 대한 일정 정보 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85546bc93e6626bfcc85a28f06a4c2fe24fe9fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660850"
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a><span data-ttu-id="1f891-102">Change the Scheduling Details for a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="1f891-102">Change the Scheduling Details for a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="1f891-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 작업 정의에 대한 일정 정보를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-103">This topic describes how to change the scheduling details for a job definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1f891-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1f891-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1f891-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1f891-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1f891-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1f891-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1f891-107">보안</span><span class="sxs-lookup"><span data-stu-id="1f891-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1f891-108">**다음을 사용하여 작업 정의에 대한 일정 정보를 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="1f891-108">**To change the scheduling details for a job definition, using:**</span></span>  
  
     [<span data-ttu-id="1f891-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f891-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1f891-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f891-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f891-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1f891-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1f891-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1f891-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1f891-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 마스터 작업은 로컬 및 원격 서버 모두에서 대상이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f891-114">보안</span><span class="sxs-lookup"><span data-stu-id="1f891-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f891-115">권한</span><span class="sxs-lookup"><span data-stu-id="1f891-115">Permissions</span></span>  
 <span data-ttu-id="1f891-116">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="1f891-117">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f891-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1f891-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1f891-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="1f891-119">작업 정의에 대한 일정 정보를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="1f891-119">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="1f891-120">**개체 탐색기** 에서 더하기 기호를 클릭하여 편집하려는 일정이 지정된 작업이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-120">In **Object Explorer,** click the plus sign to expand the server that contains the job whose schedule you want to edit.</span></span>  
  
2.  <span data-ttu-id="1f891-121">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1f891-122">더하기 기호를 클릭하여 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="1f891-123">편집하려는 일정이 지정된 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-123">Right-click the job whose schedule you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="1f891-124">**작업 속성-**_job_name_ 대화 상자의 **페이지 선택**에서 **일정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Schedules**.</span></span> <span data-ttu-id="1f891-125">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;일정 페이지&#41;](job-properties-new-job-schedules-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f891-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md).</span></span>  
  
6.  <span data-ttu-id="1f891-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f891-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1f891-127">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="1f891-128">작업 정의에 대한 일정 정보를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="1f891-128">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="1f891-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1f891-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1f891-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f891-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
 <span data-ttu-id="1f891-132">자세한 내용은 [sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f891-132">For more information, see [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql).</span></span>  
  
  
