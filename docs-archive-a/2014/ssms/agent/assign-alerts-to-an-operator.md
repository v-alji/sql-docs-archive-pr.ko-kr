---
title: 운영자에게 경고 할당 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cc238b952c03595035856f377b6fdbb9eaf5e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650366"
---
# <a name="assign-alerts-to-an-operator"></a><span data-ttu-id="45237-102">운영자에게 경고 할당</span><span class="sxs-lookup"><span data-stu-id="45237-102">Assign Alerts to an Operator</span></span>
  <span data-ttu-id="45237-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는을 사용 하 여에서 작업에 대 한 알림을 받을 수 있도록 에이전트 경고를 운영자에 게 할당 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="45237-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts to operators so they can receive notifications about jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="45237-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="45237-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="45237-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="45237-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="45237-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45237-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="45237-107">보안</span><span class="sxs-lookup"><span data-stu-id="45237-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="45237-108">**다음을 사용하여 운영자에게 경고를 할당합니다.**</span><span class="sxs-lookup"><span data-stu-id="45237-108">**To assign alerts to an operator, using:**</span></span>  
  
     [<span data-ttu-id="45237-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45237-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="45237-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="45237-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="45237-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="45237-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="45237-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45237-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="45237-113">는 그래픽 방식으로 전체 경고 시스템을 간편하게 관리할 수 있도록 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45237-113">provides an easy, graphical way to manage the entire alerting system.</span></span> <span data-ttu-id="45237-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하면 경고 인프라를 쉽게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45237-114">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is the recommended way to configure your alert infrastructure.</span></span>  
  
-   <span data-ttu-id="45237-115">경고에 대한 응답으로 알림을 보내려면 먼저 메일을 보낼 수 있도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-115">To send a notification in response to an alert, you must first configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send mail.</span></span> <span data-ttu-id="45237-116">자세한 내용은 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45237-116">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
-   <span data-ttu-id="45237-117">전자 메일 메시지 또는 호출기 알림을 전송하는 동안 오류가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 오류 로그에 오류가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="45237-117">If a failure occurs when sending an e-mail message or pager notification, the failure is reported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service error log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45237-118">보안</span><span class="sxs-lookup"><span data-stu-id="45237-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45237-119">권한</span><span class="sxs-lookup"><span data-stu-id="45237-119">Permissions</span></span>  
 <span data-ttu-id="45237-120">**sysadmin** 고정 서버 역할의 멤버만 운영자에 경고를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45237-120">Only members of the **sysadmin** fixed server role can assign alerts to operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45237-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="45237-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="45237-122">운영자에게 경고를 할당하려면</span><span class="sxs-lookup"><span data-stu-id="45237-122">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="45237-123">**개체 탐색기**에서 더하기 기호를 클릭하여 경고를 할당하려는 운영자가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator to which you want to assign an alert.</span></span>  
  
2.  <span data-ttu-id="45237-124">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="45237-125">더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="45237-126">경고를 할당하려는 운영자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 후 **알림** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-126">Right-click the operator to which you want to assign an alert and select **Properties**, and select the **Notifications** page.</span></span>  
  
5.  <span data-ttu-id="45237-127">_operator_name_**속성** 대화 상자의 **페이지 선택**에서 **알림**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-127">In the _operator_name_**Properties** dialog box, under **Select a page**, select **Notifications**.</span></span>  
  
6.  <span data-ttu-id="45237-128">**사용자에게 알림을 보내는 방법**아래에서 **경고** 를 선택하여 이 운영자에게 보내진 경고 목록을 보거나 **작업** 을 선택하여 이 운영자에게 알림을 보내는 작업 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="45237-128">Under **View notifications sent to this user by**, select **Alerts** to view a list of alerts sent to this operator or select **Jobs** to view a list of jobs that send notifications to this operator.</span></span> <span data-ttu-id="45237-129">**전자 메일**, **호출기**또는 **Net send**중 하나 이상의 확인란을 선택하여 필요에 따라 각 알림에 대한 알림 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-129">Select one or more of the following checkboxes to define the notification method for each notification as necessary: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="45237-130">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-130">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="45237-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="45237-131">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="45237-132">운영자에게 경고를 할당하려면</span><span class="sxs-lookup"><span data-stu-id="45237-132">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="45237-133">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="45237-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="45237-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45237-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="45237-136">자세한 내용은 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45237-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
