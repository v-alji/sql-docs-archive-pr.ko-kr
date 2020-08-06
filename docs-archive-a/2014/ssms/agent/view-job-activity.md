---
title: 작업 활동 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56b159952c83ed243c4c5d8012c76e5a2a248519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741544"
---
# <a name="view-job-activity"></a><span data-ttu-id="ddd36-102">작업 활동 보기</span><span class="sxs-lookup"><span data-stu-id="ddd36-102">View Job Activity</span></span>
  <span data-ttu-id="ddd36-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 작업의 런타임 상태를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-103">This topic describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ddd36-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 시작할 때 새 세션이 만들어지고 **msdb** 데이터베이스의 **sysjobactivity** 테이블에 기존에 정의된 모든 작업이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-104">When the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service starts, a new session is created and the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="ddd36-105">이 테이블은 현재 작업 활동과 상태를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-105">This table records current job activity and status.</span></span> <span data-ttu-id="ddd36-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 작업 활동 모니터를 사용하여 작업의 현재 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-106">You can use the Job Activity Monitor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to view the current state of jobs.</span></span> <span data-ttu-id="ddd36-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 예기치 않게 종료되는 경우 **sysjobactivity** 테이블을 참조하여 서비스 종료 시 어떤 작업이 실행 중이었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service unexpectedly terminates, you can refer to the **sysjobactivity** table to see which jobs were being executed when the service terminated.</span></span>  
  
 <span data-ttu-id="ddd36-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ddd36-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ddd36-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ddd36-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ddd36-110">보안</span><span class="sxs-lookup"><span data-stu-id="ddd36-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ddd36-111">**작업 활동을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="ddd36-111">**To view job activity, using:**</span></span>  
  
     [<span data-ttu-id="ddd36-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ddd36-112">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="ddd36-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ddd36-113">Transact-SQL</span></span>](#TSQL)  
  
## <a name="before-you-begin"></a><span data-ttu-id="ddd36-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ddd36-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ddd36-115">보안</span><span class="sxs-lookup"><span data-stu-id="ddd36-115">Security</span></span>  
 <span data-ttu-id="ddd36-116">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddd36-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ddd36-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ddd36-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="ddd36-118">작업 활동을 보려면</span><span class="sxs-lookup"><span data-stu-id="ddd36-118">To view job activity</span></span>  
  
1.  <span data-ttu-id="ddd36-119">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ddd36-120">**SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-120">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="ddd36-121">**작업 활동 모니터** 를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-121">Right-click **Job Activity Monitor** and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="ddd36-122">**작업 활동 모니터**에서 이 서버에 정의되어 있는 각 작업에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-122">In the **Job Activity Monitor**, you can view details about each job that is defined for this server.</span></span>  
  
5.  <span data-ttu-id="ddd36-123">작업을 시작하거나 중지하거나, 활성화하거나 비활성화하거나, 작업 활동 모니터에 표시된 작업 상태를 새로 고치거나, 작업을 삭제하거나 작업의 기록 또는 속성을 보려면 작업을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-123">Right-click a job to start it, stop it, enable or disable it, refresh its status as displayed in the Job Activity Monitor, delete it, or view its history or properties.</span></span>  <span data-ttu-id="ddd36-124">여러 작업을 시작하거나 중지하거나, 활성화하거나 비활성화하거나 새로 고치려면 작업 활동 모니터에서 여러 행을 선택한 다음 선택 사항을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-124">To start, stop, enable or disable, or refresh multiple jobs, select multiple rows in the Job Activity Monitor, and right-click your selection.</span></span>  
  
6.  <span data-ttu-id="ddd36-125">작업 활동 모니터를 업데이트하려면 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-125">To update the Job Activity Monitor, click **Refresh**.</span></span> <span data-ttu-id="ddd36-126">더 적은 수의 행을 보려면 **필터** 를 클릭하고 필터 매개 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-126">To view fewer rows, click **Filter** and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ddd36-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ddd36-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="ddd36-128">작업 활동을 보려면</span><span class="sxs-lookup"><span data-stu-id="ddd36-128">To view job activity</span></span>  
  
1.  <span data-ttu-id="ddd36-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ddd36-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ddd36-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd36-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 <span data-ttu-id="ddd36-132">자세한 내용은 [sp_help_jobactivity &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ddd36-132">For more information, see [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).</span></span>  
  
  
