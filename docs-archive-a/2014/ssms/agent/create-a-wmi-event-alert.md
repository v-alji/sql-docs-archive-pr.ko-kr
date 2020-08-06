---
title: WMI 이벤트 경고 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: stevestein
ms.author: sstein
ms.openlocfilehash: 737e7ccac9c92e663040e71339aa120f8db8b80b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652538"
---
# <a name="create-a-wmi-event-alert"></a><span data-ttu-id="90b05-102">WMI 이벤트 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="90b05-102">Create a WMI Event Alert</span></span>
  <span data-ttu-id="90b05-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 서버 이벤트용 WMI 공급자가 모니터링하여 특정 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 이벤트가 발생할 때 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 경고를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-103">This topic describes how to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] event occurs that is monitored by the WMI Provider for Server Events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="90b05-104">WMI 공급자를 사용 하 여 이벤트를 모니터링 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [서버 이벤트 용 Wmi 공급자 개념](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="90b05-104">For information about the using the WMI Provider to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span> <span data-ttu-id="90b05-105">WMI 이벤트 경고 알림을 받는 데 필요한 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 서비스의 계정 선택](select-an-account-for-the-sql-server-agent-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90b05-105">For information about the permissions necessary to receive WMI event alert notifications, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span> <span data-ttu-id="90b05-106">WQL에 대한 자세한 내용은 [서버 이벤트용 WMI 공급자에 WQL 사용](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90b05-106">For more information about WQL, see [Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).</span></span>  
  
 <span data-ttu-id="90b05-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="90b05-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90b05-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="90b05-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90b05-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="90b05-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="90b05-110">보안</span><span class="sxs-lookup"><span data-stu-id="90b05-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90b05-111">**다음을 사용하여 WMI 이벤트 경고를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="90b05-111">**To create a WMI event alert, using:**</span></span>  
  
     [<span data-ttu-id="90b05-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90b05-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90b05-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90b05-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90b05-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="90b05-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="90b05-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="90b05-115">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="90b05-116">는 전체 경고 시스템을 간편하게 그래픽 방식으로 관리할 수 있도록 해 줄 뿐만 아니라 경고 인프라를 구성하는 데 있어서도 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-116">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="90b05-117">master 데이터베이스에서 **xp_logevent** 로 생성된 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-117">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="90b05-118">따라서 경고에 대한 **xp_logevent** 이 **@database_name** 또는 NULL이 아닌 경우 **xp_logevent** 는 경고를 트리거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-118">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="90b05-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 실행하는 컴퓨터의 WMI 네임스페이스만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-119">Only WMI namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90b05-120">보안</span><span class="sxs-lookup"><span data-stu-id="90b05-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90b05-121">권한</span><span class="sxs-lookup"><span data-stu-id="90b05-121">Permissions</span></span>  
 <span data-ttu-id="90b05-122">기본적으로 **sysadmin** 고정 서버 역할의 멤버만 **sp_add_alert**를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-122">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90b05-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="90b05-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="90b05-124">WMI 이벤트 경고를 만들려면</span><span class="sxs-lookup"><span data-stu-id="90b05-124">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="90b05-125">**개체 탐색기** 에서 더하기 기호를 클릭하여 WMI 이벤트 경고를 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-125">In **Object Explorer,** click the plus sign to expand the server where you want to create a WMI event alert.</span></span>  
  
2.  <span data-ttu-id="90b05-126">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-126">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="90b05-127">**경고** 를 마우스 오른쪽 단추로 클릭하고 **새 경고**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-127">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="90b05-128">**새 경고** 대화 상자의 **이름** 상자에 이 경고의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-128">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="90b05-129">**사용** 확인란을 선택하여 경고를 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-129">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="90b05-130">기본적으로 **사용** 이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-130">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="90b05-131">**유형** 목록에서 **WMI 이벤트 경고**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-131">In the **Type** list, select **WMI event alert**.</span></span>  
  
7.  <span data-ttu-id="90b05-132">**WMI 이벤트 경고 정의**의 **네임스페이스** 상자에 이 경고를 트리거할 WMI 이벤트를 식별하는 WQL(WMI Query Language) 문에 대한 WMI 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-132">Under **WMI event alert definition**, in the **Namespace** box, specify the WMI namespace for the WMI Query Language (WQL) statement that identifies which WMI event will trigger this alert.</span></span>  
  
8.  <span data-ttu-id="90b05-133">**쿼리** 상자에 이 경고가 응답하는 이벤트를 식별할 WQL 문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-133">In the **Query** box, specify the WQL statement that identifies the event that this alert responds to.</span></span>  
  
9. <span data-ttu-id="90b05-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90b05-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="90b05-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="90b05-136">WMI 이벤트 경고를 만들려면</span><span class="sxs-lookup"><span data-stu-id="90b05-136">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="90b05-137">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90b05-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90b05-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90b05-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information...',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
 <span data-ttu-id="90b05-140">자세한 내용은 [sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="90b05-140">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
