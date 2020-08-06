---
title: 운영자 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfe07042f9a4b8ac595ada8b86e7bad131032700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731379"
---
# <a name="create-an-operator"></a><span data-ttu-id="47082-102">운영자 만들기</span><span class="sxs-lookup"><span data-stu-id="47082-102">Create an Operator</span></span>
  <span data-ttu-id="47082-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는을 사용 하 여에서 에이전트 작업에 대 한 알림을 받도록 사용자를 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="47082-103">This topic describes how to configure a user to receive notifications about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="47082-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="47082-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="47082-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="47082-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="47082-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="47082-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="47082-107">보안</span><span class="sxs-lookup"><span data-stu-id="47082-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="47082-108">**운영자를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="47082-108">**To create an operator, using:**</span></span>  
  
     [<span data-ttu-id="47082-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47082-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="47082-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47082-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="47082-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="47082-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="47082-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="47082-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="47082-113">**이후 버전에서는** 에이전트에서 호출기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="47082-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="47082-114">새 개발 작업에서는 이 기능을 사용하지 말고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="47082-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="47082-115">SQL Server 에이전트는 데이터베이스 메일을 사용하여 운영자에게 전자 메일 및 호출기 알림을 보내도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="47082-116">자세한 내용은 [경고를 운영자에게 할당](assign-alerts-to-an-operator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47082-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="47082-117">는 작업 구조를 만들고 관리할 수 있는 바람직한 방법을 제공하는데 이는 그래픽을 사용하여 쉽게 작업을 관리할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="47082-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="47082-118">보안</span><span class="sxs-lookup"><span data-stu-id="47082-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="47082-119">권한</span><span class="sxs-lookup"><span data-stu-id="47082-119">Permissions</span></span>  
 <span data-ttu-id="47082-120">**sysadmin** 고정 서버 역할의 멤버만이 운영자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47082-120">Only members of the **sysadmin** fixed server role can create operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="47082-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="47082-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="47082-122">운영자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="47082-122">To create an operator</span></span>  
  
1.  <span data-ttu-id="47082-123">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트 운영자를 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-123">In **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent operator.</span></span>  
  
2.  <span data-ttu-id="47082-124">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="47082-125">**운영자** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 운영자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-125">Right-click the **Operators** folder and select **New Operator**.</span></span>  
  
     <span data-ttu-id="47082-126">**새 운영자** 대화 상자의 **일반** 페이지에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="47082-126">The following options are available on the **General** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="47082-127">**이름**</span><span class="sxs-lookup"><span data-stu-id="47082-127">**Name**</span></span>  
     <span data-ttu-id="47082-128">운영자의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-128">Change the name of the operator.</span></span>  
  
     <span data-ttu-id="47082-129">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="47082-129">**Enabled**</span></span>  
     <span data-ttu-id="47082-130">운영자를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-130">Enable the operator.</span></span> <span data-ttu-id="47082-131">활성화하지 않으면 해당 운영자에게 알림이 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47082-131">When not enabled, no notifications are sent to the operator.</span></span>  
  
     <span data-ttu-id="47082-132">**전자 메일 이름**</span><span class="sxs-lookup"><span data-stu-id="47082-132">**E-mail name**</span></span>  
     <span data-ttu-id="47082-133">운영자의 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-133">Specifies the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="47082-134">**Net Send 주소**</span><span class="sxs-lookup"><span data-stu-id="47082-134">**Net send address**</span></span>  
     <span data-ttu-id="47082-135">**net send**에 사용할 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-135">Specify the address to use for **net send**.</span></span>  
  
     <span data-ttu-id="47082-136">**호출기 전자 메일 이름**</span><span class="sxs-lookup"><span data-stu-id="47082-136">**Pager e-mail name**</span></span>  
     <span data-ttu-id="47082-137">운영자의 호출기에 사용할 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-137">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
     <span data-ttu-id="47082-138">**호출기 연락 가능 근무 일정**</span><span class="sxs-lookup"><span data-stu-id="47082-138">**Pager on duty schedule**</span></span>  
     <span data-ttu-id="47082-139">호출기로 연락 가능한 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-139">Sets the times at which the pager is active.</span></span>  
  
     <span data-ttu-id="47082-140">**월요일 - 일요일**</span><span class="sxs-lookup"><span data-stu-id="47082-140">**Monday - Sunday**</span></span>  
     <span data-ttu-id="47082-141">호출기로 연락 가능한 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-141">Select the days that the pager is active.</span></span>  
  
     <span data-ttu-id="47082-142">**업무 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="47082-142">**Workday begin**</span></span>  
     <span data-ttu-id="47082-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 호출기로 메시지를 보내기 시작하는 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-143">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
     <span data-ttu-id="47082-144">**업무 종료 시간**</span><span class="sxs-lookup"><span data-stu-id="47082-144">**Workday end**</span></span>  
     <span data-ttu-id="47082-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 호출기로 메시지를 더 이상 보내지 않는 기준 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-145">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
     <span data-ttu-id="47082-146">**새 운영자** 대화 상자의 **알림** 페이지에는 다음과 같은 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="47082-146">The following options are available on the **Notifications** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="47082-147">**경고**</span><span class="sxs-lookup"><span data-stu-id="47082-147">**Alerts**</span></span>  
     <span data-ttu-id="47082-148">인스턴스의 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-148">View the alerts in the instance.</span></span>  
  
     <span data-ttu-id="47082-149">**작업**</span><span class="sxs-lookup"><span data-stu-id="47082-149">**Jobs**</span></span>  
     <span data-ttu-id="47082-150">인스턴스의 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-150">View the jobs in the instance.</span></span>  
  
     <span data-ttu-id="47082-151">**경고 목록**</span><span class="sxs-lookup"><span data-stu-id="47082-151">**Alert list**</span></span>  
     <span data-ttu-id="47082-152">인스턴스의 경고를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-152">Lists the alerts in the instance.</span></span>  
  
     <span data-ttu-id="47082-153">**작업 목록**</span><span class="sxs-lookup"><span data-stu-id="47082-153">**Job list**</span></span>  
     <span data-ttu-id="47082-154">인스턴스의 작업을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-154">Lists the jobs in the instance.</span></span>  
  
     <span data-ttu-id="47082-155">**주소**</span><span class="sxs-lookup"><span data-stu-id="47082-155">**E-mail**</span></span>  
     <span data-ttu-id="47082-156">전자 메일을 사용하여 이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="47082-156">Notify this operator using e-mail.</span></span>  
  
     <span data-ttu-id="47082-157">**호출기**</span><span class="sxs-lookup"><span data-stu-id="47082-157">**Pager**</span></span>  
     <span data-ttu-id="47082-158">호출기 주소로 전자 메일을 보내 이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="47082-158">Notify this operator by sending e-mail to the pager address.</span></span>  
  
     <span data-ttu-id="47082-159">**Net Send**</span><span class="sxs-lookup"><span data-stu-id="47082-159">**Net send**</span></span>  
     <span data-ttu-id="47082-160">**net send**를 사용하여 이 운영자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="47082-160">Notify this operator using **net send**.</span></span>  
  
4.  <span data-ttu-id="47082-161">새 운영자 만들기를 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-161">When finished creating the new operator, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="47082-162">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="47082-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="47082-163">운영자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="47082-163">To create an operator</span></span>  
  
1.  <span data-ttu-id="47082-164">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="47082-165">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="47082-166">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47082-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 <span data-ttu-id="47082-167">자세한 내용은 [sp_add_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47082-167">For more information, see [sp_add_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).</span></span>  
  
  
