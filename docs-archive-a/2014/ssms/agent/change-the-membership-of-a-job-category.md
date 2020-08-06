---
title: 작업 범주의 멤버 자격 변경 | Microsoft 문서
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
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9ed0db394f63594937ad923734b07fed8050955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660851"
---
# <a name="change-the-membership-of-a-job-category"></a><span data-ttu-id="b8fef-102">Change the Membership of a Job Category</span><span class="sxs-lookup"><span data-stu-id="b8fef-102">Change the Membership of a Job Category</span></span>
  <span data-ttu-id="b8fef-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 SQL Server 관리 개체를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 작업 범주의 멤버 자격을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-103">This topic describes how to change the membership of the job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="b8fef-104">작업 범주를 사용하면 작업을 쉽게 필터링하고 그룹화할 수 있게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="b8fef-105">사용자 고유의 작업 범주를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-105">You can create your own job categories.</span></span> <span data-ttu-id="b8fef-106">또한 작업 범주에서 Microsoft SQL Server 에이전트 작업 멤버 자격을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-106">You can also change Microsoft SQL Server Agent jobs membership in job categories.</span></span>  
  
 <span data-ttu-id="b8fef-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b8fef-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b8fef-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b8fef-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b8fef-109">보안</span><span class="sxs-lookup"><span data-stu-id="b8fef-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b8fef-110">**작업 범주의 멤버 자격을 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="b8fef-110">**To change the membership of a job category, using:**</span></span>  
  
     [<span data-ttu-id="b8fef-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b8fef-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="b8fef-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b8fef-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="b8fef-113">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="b8fef-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b8fef-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b8fef-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b8fef-115">보안</span><span class="sxs-lookup"><span data-stu-id="b8fef-115">Security</span></span>  
 <span data-ttu-id="b8fef-116">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8fef-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="b8fef-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b8fef-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="b8fef-118">작업 범주의 멤버를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b8fef-118">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="b8fef-119">**개체 탐색기**에서 더하기 기호를 클릭하여 작업 범주를 편집하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-119">In **Object Explorer**, click the plus sign to expand the server where you want to edit a job category.</span></span>  
  
2.  <span data-ttu-id="b8fef-120">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b8fef-121">**작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 범주 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-121">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="b8fef-122">**작업 범주 관리**_server_name_ 대화 상자에서 편집하려는 작업 범주를 선택한 다음 **작업 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-122">In the **Manage Job Categories**_server_name_ dialog box, select the job category that you want to edit, and then click **View Jobs**.</span></span>  
  
5.  <span data-ttu-id="b8fef-123">**모든 작업 표시** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-123">Select the **Show all jobs** check box.</span></span>  
  
6.  <span data-ttu-id="b8fef-124">범주에 작업을 추가하려면 주 표 형태의 **선택** 열에서 해당 작업에 대한 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-124">To add a job to the category, in the main grid, select the check box in the **Select** column corresponding to the job.</span></span> <span data-ttu-id="b8fef-125">범주에서 작업을 제거하려면 해당 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-125">To remove a job from the category, clear the box.</span></span> <span data-ttu-id="b8fef-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-126">When finished, click **OK**.</span></span>  
  
7.  <span data-ttu-id="b8fef-127">**작업 범주 관리**_server_name_ 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-127">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="b8fef-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b8fef-128">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="b8fef-129">작업 범주의 멤버를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b8fef-129">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="b8fef-130">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b8fef-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b8fef-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="b8fef-133">자세한 내용은 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8fef-133">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="b8fef-134">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="b8fef-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="b8fef-135">**작업 범주의 멤버를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="b8fef-135">**To change the membership of a job category**</span></span>  
  
 <span data-ttu-id="b8fef-136">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCategory` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fef-136">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
