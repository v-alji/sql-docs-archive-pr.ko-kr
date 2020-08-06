---
title: 작업 범주에 작업 할당 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 208ff6722a9c18fd4dd0d061575f0d496af27810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660854"
---
# <a name="assign-a-job-to-a-job-category"></a><span data-ttu-id="ef2e6-102">작업 범주에 작업 할당</span><span class="sxs-lookup"><span data-stu-id="ef2e6-102">Assign a Job to a Job Category</span></span>
  <span data-ttu-id="ef2e6-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 작업 범주에 에이전트 작업을 할당 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ef2e6-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to job categories in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="ef2e6-104">작업 범주를 사용하면 작업을 쉽게 필터링하고 그룹화할 수 있게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="ef2e6-105">예를 들어 데이터베이스 유지 관리 범주에 있는 모든 데이터베이스 백업 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="ef2e6-106">작업을 기본 제공 작업 범주에 할당하거나 사용자 정의 작업 범주를 만든 다음 여기에 작업을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-106">You can assign jobs to built-in job categories, or you can create a user-defined job category and then assign jobs to that.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef2e6-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ef2e6-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef2e6-108">보안</span><span class="sxs-lookup"><span data-stu-id="ef2e6-108">Security</span></span>  
 <span data-ttu-id="ef2e6-109">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-109">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ef2e6-110">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ef2e6-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="ef2e6-111">작업 범주에 작업을 할당하려면</span><span class="sxs-lookup"><span data-stu-id="ef2e6-111">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="ef2e6-112">**개체 탐색기**에서 더하기 기호를 클릭하여 작업을 작업 범주에 할당하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-112">In **Object Explorer**, click the plus sign to expand the server where you want to assign a job to a job category.</span></span>  
  
2.  <span data-ttu-id="ef2e6-113">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-113">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="ef2e6-114">더하기 기호를 클릭하여 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-114">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="ef2e6-115">편집할 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-115">Right-click the job you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="ef2e6-116">**작업 속성-**_Job_name_ 대화 상자의 **범주** 목록에서 작업에 할당 하려는 작업 범주를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-116">In the **Job Properties -**_job_name_ dialog box, in the **Category** list, select the job category you want to assign to the job.</span></span>  
  
6.  <span data-ttu-id="ef2e6-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-117">Click **OK**.</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ef2e6-118">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ef2e6-118">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="ef2e6-119">작업 범주에 작업을 할당하려면</span><span class="sxs-lookup"><span data-stu-id="ef2e6-119">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="ef2e6-120">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef2e6-121">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef2e6-122">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="ef2e6-123">자세한 내용은 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-123">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="ef2e6-124">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="ef2e6-124">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="ef2e6-125">**작업 범주에 작업을 할당하려면**</span><span class="sxs-lookup"><span data-stu-id="ef2e6-125">**To assign a job to a job category**</span></span>  
  
 <span data-ttu-id="ef2e6-126">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCategory` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2e6-126">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
  
  
