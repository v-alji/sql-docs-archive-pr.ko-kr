---
title: 작업을 사용하지 않거나 사용하도록 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42fe7cbeed1e2ff3f93b1afef52b165a7d660ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639231"
---
# <a name="disable-or-enable-a-job"></a><span data-ttu-id="001e7-102">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="001e7-102">Disable or Enable a Job</span></span>
  <span data-ttu-id="001e7-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 작업을 비활성화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-103">This topic describes how to disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="001e7-104">작업을 사용하지 않도록 설정하더라도 해당 작업은 삭제되지 않으며 필요할 때 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-104">When you disable a job, it is not deleted and can be enabled again when necessary.</span></span>  
  
 <span data-ttu-id="001e7-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="001e7-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="001e7-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="001e7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="001e7-107">보안</span><span class="sxs-lookup"><span data-stu-id="001e7-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="001e7-108">**작업을 사용하지 않거나 사용하도록 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="001e7-108">**To disable or enable a job, using:**</span></span>  
  
     [<span data-ttu-id="001e7-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="001e7-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="001e7-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="001e7-110">Transact-SQL</span></span>](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="001e7-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="001e7-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="001e7-112">보안</span><span class="sxs-lookup"><span data-stu-id="001e7-112">Security</span></span>  
 <span data-ttu-id="001e7-113">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="001e7-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="001e7-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="001e7-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="001e7-115">작업을 사용하지 않거나 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="001e7-115">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="001e7-116">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-116">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="001e7-117">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-117">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="001e7-118">**작업**을 확장한 다음 사용하지 않거나 사용하도록 설정할 작업을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-118">Expand **Jobs**, and then right-click the job that you want to disable or enable.</span></span>  
  
4.  <span data-ttu-id="001e7-119">작업을 사용하지 않도록 설정하려면 **사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-119">To disable a job, click **Disable**.</span></span> <span data-ttu-id="001e7-120">작업을 사용하도록 설정하려면 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-120">To enable a job, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="001e7-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="001e7-121">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="001e7-122">작업을 사용하지 않거나 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="001e7-122">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="001e7-123">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="001e7-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="001e7-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="001e7-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="001e7-126">자세한 내용은 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="001e7-126">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
