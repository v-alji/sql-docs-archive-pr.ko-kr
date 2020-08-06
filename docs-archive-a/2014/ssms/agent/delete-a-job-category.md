---
title: 작업 범주 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e96dd0461f3dace138b7822cdbaaa2fa242e2cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729008"
---
# <a name="delete-a-job-category"></a><span data-ttu-id="138f6-102">작업 범주 삭제</span><span class="sxs-lookup"><span data-stu-id="138f6-102">Delete a Job Category</span></span>
  <span data-ttu-id="138f6-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 범주를 삭제 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="138f6-103">This topic describes how to delete a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="138f6-104">작업 범주를 사용하면 작업을 쉽게 필터링하고 그룹화할 수 있게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="138f6-105">예를 들어 데이터베이스 유지 관리 범주에 있는 모든 데이터베이스 백업 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span>  

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="138f6-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="138f6-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="138f6-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="138f6-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="138f6-108">사용자가 정의한 작업 범주를 삭제할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 이 작업 범주에 할당된 작업을 다른 작업 범주에 재할당할 것인지 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-108">When you delete a user-defined job category, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prompts you to reassign the jobs that are assigned to it to another job category.</span></span> <span data-ttu-id="138f6-109">사용자가 정의한 작업 범주만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-109">You can only delete user-defined job categories.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="138f6-110">보안</span><span class="sxs-lookup"><span data-stu-id="138f6-110">Security</span></span>  
 <span data-ttu-id="138f6-111">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="138f6-111">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="138f6-112">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="138f6-112">Using SQL Server Management Studio</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="138f6-113">작업 범주를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="138f6-113">To delete a job category</span></span>  
  
1.  <span data-ttu-id="138f6-114">**개체 탐색기**에서 더하기 기호를 클릭하여 작업 범주를 삭제하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-114">In **Object Explorer**, click the plus sign to expand the server where you want to delete a job category.</span></span>  
  
2.  <span data-ttu-id="138f6-115">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-115">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="138f6-116">**작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 범주 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-116">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="138f6-117">**작업 범주 관리**_server_name_ 대화 상자에서 삭제할 작업 범주를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-117">In the **Manage Job Categories**_server_name_ dialog box, select the job category to delete.</span></span>  
  
5.  <span data-ttu-id="138f6-118">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-118">Click **Delete**.</span></span>  
  
6.  <span data-ttu-id="138f6-119">**작업 범주** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-119">In the **Job Categories** dialog box, click **Yes**.</span></span>  
  
7.  <span data-ttu-id="138f6-120">**작업 범주 관리**_server_name_ 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-120">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="138f6-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="138f6-121">Using Transact-SQL</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="138f6-122">작업 범주를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="138f6-122">To delete a job category</span></span>  
  
1.  <span data-ttu-id="138f6-123">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="138f6-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="138f6-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 <span data-ttu-id="138f6-126">자세한 내용은 [sp_delete_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="138f6-126">For more information, see [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).</span></span>  

  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="138f6-127">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="138f6-127">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-a-job-category"></a><span data-ttu-id="138f6-128">작업 범주를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="138f6-128">To delete a job category</span></span>
  
 <span data-ttu-id="138f6-129">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCategory` 클래스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="138f6-129">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
