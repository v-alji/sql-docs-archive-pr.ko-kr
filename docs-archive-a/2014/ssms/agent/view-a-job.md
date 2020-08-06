---
title: 작업 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 26406aaf2ba0ac4809eb7ac2c84799469d0468d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661486"
---
# <a name="view-a-job"></a><span data-ttu-id="e4b91-102">View a Job</span><span class="sxs-lookup"><span data-stu-id="e4b91-102">View a Job</span></span>
  <span data-ttu-id="e4b91-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는을 사용 하 여에서 에이전트 작업을 보는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e4b91-103">This topic describes how to view [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e4b91-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e4b91-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e4b91-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e4b91-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e4b91-106">보안</span><span class="sxs-lookup"><span data-stu-id="e4b91-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e4b91-107">**작업을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="e4b91-107">**To view a job, using:**</span></span>  
  
     [<span data-ttu-id="e4b91-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4b91-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="e4b91-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4b91-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="e4b91-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="e4b91-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4b91-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e4b91-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4b91-112">보안</span><span class="sxs-lookup"><span data-stu-id="e4b91-112">Security</span></span>  
 <span data-ttu-id="e4b91-113">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-113">You can only view jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="e4b91-114">이 역할의 멤버는 모든 작업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-114">Members of this role can view all jobs.</span></span> <span data-ttu-id="e4b91-115">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4b91-115">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e4b91-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e4b91-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="e4b91-117">작업을 보려면</span><span class="sxs-lookup"><span data-stu-id="e4b91-117">To view a job</span></span>  
  
1.  <span data-ttu-id="e4b91-118">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e4b91-119">**SQL Server 에이전트**를 확장한 다음 **작업**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-119">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="e4b91-120">작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-120">Right-click a job, and then click **Properties**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="e4b91-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e4b91-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="e4b91-122">작업을 보려면</span><span class="sxs-lookup"><span data-stu-id="e4b91-122">To view a job</span></span>  
  
1.  <span data-ttu-id="e4b91-123">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4b91-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4b91-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="e4b91-126">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="e4b91-126">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="e4b91-127">**작업을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e4b91-127">**To view a job**</span></span>  
  
 <span data-ttu-id="e4b91-128">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Job` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4b91-128">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="e4b91-129">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4b91-129">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
