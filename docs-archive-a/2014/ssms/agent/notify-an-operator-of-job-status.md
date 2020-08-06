---
title: 운영자에게 작업 상태 알리기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
ms.openlocfilehash: a202327ad63cf7ef8f51d3572b257816ee6d9419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649328"
---
# <a name="notify-an-operator-of-job-status"></a><span data-ttu-id="d687c-102">Notify an Operator of Job Status</span><span class="sxs-lookup"><span data-stu-id="d687c-102">Notify an Operator of Job Status</span></span>
  <span data-ttu-id="d687c-103">이 항목에서는, 또는 SQL Server 관리 개체를 사용 하 여에서 알림 옵션을 설정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 그러면 에이전트에서 작업에 대해 운영자에 게 알림을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-103">This topic describes how to set notification options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects, so [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can send notifications to operators about jobs.</span></span>  
  
 <span data-ttu-id="d687c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d687c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d687c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d687c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d687c-106">보안</span><span class="sxs-lookup"><span data-stu-id="d687c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d687c-107">**운영자에게 작업 상태를 알리려면:**</span><span class="sxs-lookup"><span data-stu-id="d687c-107">**To notify an operator of job status, using:**</span></span>  
  
     [<span data-ttu-id="d687c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d687c-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="d687c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d687c-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="d687c-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="d687c-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d687c-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d687c-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d687c-112">보안</span><span class="sxs-lookup"><span data-stu-id="d687c-112">Security</span></span>  
 <span data-ttu-id="d687c-113">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d687c-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d687c-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d687c-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="d687c-115">운영자에게 작업 상태를 알리려면</span><span class="sxs-lookup"><span data-stu-id="d687c-115">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="d687c-116">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d687c-117">**SQL Server 에이전트**, **작업**을 차례로 확장한 다음 편집할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-117">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d687c-118">**작업 속성** 대화 상자에서 **알림** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-118">In the **Job Properties** dialog box, select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="d687c-119">전자 메일을 통해 운영자에게 알리려면 **전자 메일**확인란을 선택하고 목록에서 운영자를 선택한 후 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-119">If you want to notify an operator by e-mail, check **E-mail**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="d687c-120">**작업 성공 시** - 작업이 성공적으로 완료되면 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-120">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="d687c-121">**작업 실패 시** - 작업이 성공적으로 완료되지 않았을 때 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-121">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="d687c-122">**작업 완료 시** - 완료 상태에 관계없이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-122">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
5.  <span data-ttu-id="d687c-123">무선 호출기를 통해 운영자에게 알리려면 **호출**확인란을 선택하고 목록에서 운영자를 선택한 후 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-123">If you want to notify an operator by pager, check **Page**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="d687c-124">**작업 성공 시** - 작업이 성공적으로 완료되면 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-124">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="d687c-125">**작업 실패 시** - 작업이 성공적으로 완료되지 않았을 때 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-125">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="d687c-126">**작업 완료 시** - 완료 상태에 관계없이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-126">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
6.  <span data-ttu-id="d687c-127">Net Send로 운영자에게 알리려면 **Net Send**확인란을 선택하고 목록에서 운영자를 선택한 후 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-127">If you want to notify an operator by net send, check **Net send**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="d687c-128">**작업 성공 시** - 작업이 성공적으로 완료되면 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-128">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="d687c-129">**작업 실패 시** - 작업이 성공적으로 완료되지 않았을 때 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-129">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="d687c-130">**작업 완료 시** - 완료 상태에 관계없이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-130">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="d687c-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d687c-131">Using Transact-SQL</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="d687c-132">운영자에게 작업 상태를 알리려면</span><span class="sxs-lookup"><span data-stu-id="d687c-132">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="d687c-133">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d687c-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d687c-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="d687c-136">자세한 내용은 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d687c-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="d687c-137">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="d687c-137">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="d687c-138">**운영자에게 작업 상태를 알리려면**</span><span class="sxs-lookup"><span data-stu-id="d687c-138">**To notify an operator of job status**</span></span>  
  
 <span data-ttu-id="d687c-139">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Job` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d687c-139">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="d687c-140">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d687c-140">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
