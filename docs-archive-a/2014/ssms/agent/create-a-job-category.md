---
title: 작업 범주 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f6daeeca6253861e8a9dcbb72faa2bd55eb2761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735844"
---
# <a name="create-a-job-category"></a><span data-ttu-id="92d2b-102">작업 범주 만들기</span><span class="sxs-lookup"><span data-stu-id="92d2b-102">Create a Job Category</span></span>
  <span data-ttu-id="92d2b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 관리 개체를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 작업 범주를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-103">This topic describes how to create a job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92d2b-104">에이전트에는 기본으로 제공되는 작업 범주가 있으며 이를 사용하여 작업을 할당하거나 작업 범주를 만들어 작업을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-104">Agent provides built-in job categories that you can assign jobs to, or you can create a job category and assign jobs to it.</span></span> <span data-ttu-id="92d2b-105">작업 범주를 사용하면 작업을 쉽게 필터링하고 그룹화할 수 있게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-105">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="92d2b-106">예를 들어 데이터베이스 유지 관리 범주에 있는 모든 데이터베이스 백업 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-106">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="92d2b-107">사용자 고유의 작업 범주를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-107">You can also create your own job categories.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="92d2b-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="92d2b-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="92d2b-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="92d2b-109">Limitations and Restrictions</span></span>  
 <span data-ttu-id="92d2b-110">다중 서버 범주는 마스터 서버에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-110">Multiserver categories exist only on a master server.</span></span> <span data-ttu-id="92d2b-111">한 마스터 서버에서는 하나의 기본 작업 범주만 사용할 수 있습니다. 즉, [**범주화되지 않음(다중 서버)**] 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-111">There is only one default job category available on a master server: [**Uncategorized (Multi-Server)**].</span></span> <span data-ttu-id="92d2b-112">다중 서버 작업을 다운로드하면 해당 범주가 대상 서버에서 **MSX의 작업** 으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-112">When a multiserver job is downloaded, its category is changed to **Jobs From MSX** at the target server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="92d2b-113">보안</span><span class="sxs-lookup"><span data-stu-id="92d2b-113">Security</span></span>  
 <span data-ttu-id="92d2b-114">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d2b-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="92d2b-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="92d2b-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="92d2b-116">작업 범주를 만들려면</span><span class="sxs-lookup"><span data-stu-id="92d2b-116">To create a job category</span></span>  
  
1.  <span data-ttu-id="92d2b-117">**개체 탐색기**에서 더하기 기호를 클릭하여 작업 범주를 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-117">In **Object Explorer**, click the plus sign to expand the server where you want to create a job category.</span></span>  
  
2.  <span data-ttu-id="92d2b-118">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="92d2b-119">**작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 범주 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-119">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="92d2b-120">**작업 범주 관리**_server_name_ 대화 상자에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-120">In the **Manage Job Categories**_server_name_ dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="92d2b-121">새 대화 상자의 **이름** 상자에서 새 작업 범주의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-121">In the new dialog box, in the **Name** box, enter a name for the new job category.</span></span>  
  
6.  <span data-ttu-id="92d2b-122">**모든 작업 표시** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-122">Select the **Show all jobs** check box.</span></span> <span data-ttu-id="92d2b-123">새 범주에 대한 작업을 해당 확인란을 선택하여 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-123">Select one or more jobs for the new category by checking the boxes corresponding to the jobs.</span></span>  
  
7.  <span data-ttu-id="92d2b-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="92d2b-125">**작업 범주 관리**_server_name_ 대화 상자에서 **새로 고침** 을 클릭 하 여 새 작업 범주가 활성 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-125">In the **Manage Job Categories**_server_name_ dialog box, click **Refresh** to ensure that the new job category is active.</span></span> <span data-ttu-id="92d2b-126">모든 항목이 예상대로 되어 있으면 이 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-126">If everything looks as expected, close this dialog box.</span></span>  
  
 <span data-ttu-id="92d2b-127">이러한 대화 상자에 대 한 자세한 내용은 [작업 범주: 작업](job-categories-manage-job-categories.md) 범주 및 [작업 범주 관리 속성 및 새 작업 범주](job-categories-properties-new-job-category.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92d2b-127">For more information on these dialog boxes, see [Job Categories: Manage Job Categories](job-categories-manage-job-categories.md) and [Job Categories Properties and New Job Category](job-categories-properties-new-job-category.md).</span></span>  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="92d2b-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="92d2b-128">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="92d2b-129">작업 범주를 만들려면</span><span class="sxs-lookup"><span data-stu-id="92d2b-129">To create a job category</span></span>  
  
1.  <span data-ttu-id="92d2b-130">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="92d2b-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="92d2b-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="92d2b-133">자세한 내용은 [sp_add_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92d2b-133">For more information, see [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="92d2b-134">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="92d2b-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="92d2b-135">**작업 범주를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="92d2b-135">**To create a job category**</span></span>  
  
 <span data-ttu-id="92d2b-136">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCategory` 클래스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="92d2b-136">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="92d2b-137">예제 코드를 보려면 [SQL Server 에이전트에서 자동 관리 태스크 예약](sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92d2b-137">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
