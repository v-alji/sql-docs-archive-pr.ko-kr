---
title: 하나 이상의 작업 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 436625f9ad629a6b0e574aa046059f4e7e9c2bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646809"
---
# <a name="delete-one-or-more-jobs"></a><span data-ttu-id="55f49-102">하나 이상의 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="55f49-102">Delete One or More Jobs</span></span>
  <span data-ttu-id="55f49-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업을 삭제 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="55f49-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="55f49-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="55f49-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="55f49-105">보안</span><span class="sxs-lookup"><span data-stu-id="55f49-105">Security</span></span>  
 <span data-ttu-id="55f49-106">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-106">Unless you are a member of the **sysadmin** fixed server role, you can only delete jobs that you own.</span></span>  
  
 
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="55f49-107">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="55f49-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="55f49-108">작업을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="55f49-108">To delete a job</span></span>  
  
1.  <span data-ttu-id="55f49-109">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-109">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="55f49-110">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 삭제할 작업을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-110">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="55f49-111">**개체 삭제** 대화 상자에서 삭제할 작업이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-111">In the **Delete Object** dialog box, confirm that the job you intend to delete is selected.</span></span>  
  
4.  <span data-ttu-id="55f49-112">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-112">Click **OK**.</span></span>  
  
#### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="55f49-113">여러 작업을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="55f49-113">To delete multiple jobs</span></span>  
  
1.  <span data-ttu-id="55f49-114">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-114">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="55f49-115">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-115">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="55f49-116">**작업 활동 모니터**를 마우스 오른쪽 단추로 클릭 하 고 **작업 활동 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-116">Right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="55f49-117">작업 활동 모니터에서 삭제할 작업을 선택하고 마우스 오른쪽 단추로 클릭한 다음 **작업 삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-117">In the Job Activity Monitor, select the jobs you want to delete, right-click your selection, and choose **Delete jobs**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="55f49-118">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="55f49-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="55f49-119">작업을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="55f49-119">To delete a job</span></span>  
  
1.  <span data-ttu-id="55f49-120">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="55f49-121">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="55f49-122">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="55f49-123">자세한 내용은 [sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="55f49-123">For more information, see [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="55f49-124">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="55f49-124">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="55f49-125">여러 작업을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="55f49-125">To delete multiple jobs</span></span>
  
 <span data-ttu-id="55f49-126">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCollection` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="55f49-126">Use the `JobCollection` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="55f49-127">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55f49-127">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
