---
title: 심각도를 사용하여 경고 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ee353129d60fe7fc8bed0eff279920d8d4ba640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734908"
---
# <a name="create-an-alert-using-severity-level"></a><span data-ttu-id="2d251-102">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="2d251-102">Create an Alert Using Severity Level</span></span>
  <span data-ttu-id="2d251-103">이 항목에서는 또는을 사용 하 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 여에서 특정 심각도 수준의 이벤트가 발생 하는 경우 발생 하는 에이전트 경고를 만드는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2d251-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when an event of a specific severity level occurs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2d251-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2d251-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2d251-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2d251-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2d251-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2d251-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2d251-107">보안</span><span class="sxs-lookup"><span data-stu-id="2d251-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2d251-108">**다음을 통해 심각도를 사용하여 경고를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="2d251-108">**To create an alert using severity level, using:**</span></span>  
  
     [<span data-ttu-id="2d251-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d251-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2d251-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d251-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2d251-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2d251-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2d251-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2d251-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="2d251-113">는 전체 경고 시스템을 간편하게 그래픽 방식으로 관리할 수 있도록 해 줄 뿐만 아니라 경고 인프라를 구성하는 데 있어서도 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-113">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="2d251-114">master 데이터베이스에서 **xp_logevent** 로 생성된 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-114">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="2d251-115">따라서 경고에 대한 **xp_logevent** 이 **@database_name** 또는 NULL이 아닌 경우 **xp_logevent** 는 경고를 트리거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-115">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="2d251-116">19부터 25까지의 심각도를 가진 이벤트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메시지를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션 로그에 보내고 경고를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-116">Severity levels from 19 through 25 send a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log and trigger an alert.</span></span> <span data-ttu-id="2d251-117">19보다 낮은 심각도를 가진 이벤트는 **sp_altermessage**, RAISERROR WITH LOG 또는 **xp_logevent** 를 사용하여 강제로 Windows 애플리케이션 로그에 경고를 기록하도록 한 경우에만 경고를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-117">Events with severity levels less than 19 will trigger alerts only if you have used **sp_altermessage**, RAISERROR WITH LOG, or **xp_logevent** to force them to be written to the Windows application log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2d251-118">보안</span><span class="sxs-lookup"><span data-stu-id="2d251-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2d251-119">권한</span><span class="sxs-lookup"><span data-stu-id="2d251-119">Permissions</span></span>  
 <span data-ttu-id="2d251-120">기본적으로 **sysadmin** 고정 서버 역할의 멤버만 **sp_add_alert**를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-120">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2d251-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2d251-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="2d251-122">심각도를 사용하여 경고를 만들려면</span><span class="sxs-lookup"><span data-stu-id="2d251-122">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="2d251-123">**개체 탐색기** 에서 더하기 기호를 클릭하여 심각도 수준으로 경고를 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-123">In **Object Explorer,** click the plus sign to expand the server where you want to create an alert using severity level.</span></span>  
  
2.  <span data-ttu-id="2d251-124">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="2d251-125">**경고** 를 마우스 오른쪽 단추로 클릭하고 **새 경고**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-125">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="2d251-126">**새 경고** 대화 상자의 **이름** 상자에 이 경고의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-126">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="2d251-127">**유형** 목록에서 **SQL Server 이벤트 경고**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-127">In the **Type** list, select **SQL Server event alert**.</span></span>  
  
6.  <span data-ttu-id="2d251-128">**이벤트 경고 정의**아래의 **데이터베이스 이름** 목록에서 데이터베이스를 선택하여 경고를 특정 데이터베이스로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-128">Under **Event alert definition**, in the **Database name** list, select a database to restrict the alert to a specific database.</span></span>  
  
7.  <span data-ttu-id="2d251-129">**경고 발생 기준**에서 **심각도** 를 클릭한 다음 경고가 발생할 특정 심각도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-129">Under **Alerts will be raised based on**, click **Severity** and then select the specific severity that will raise the alert.</span></span>  
  
8.  <span data-ttu-id="2d251-130">**메시지에 다음 텍스트가 포함될 때 경고 발생** 에 해당하는 확인란을 선택하여 경고를 특정 문자 시퀀스로 제한한 다음 **메시지 텍스트**에 대한 키워드나 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-130">Check the box corresponding to **Raise alert when message contains** check box to restrict the alert to a particular character sequence, and then enter a keyword or character string for the **Message text**.</span></span> <span data-ttu-id="2d251-131">최대 문자 수는 100자입니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-131">The maximum number of characters is 100.</span></span>  
  
9. <span data-ttu-id="2d251-132">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-132">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2d251-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="2d251-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="2d251-134">심각도를 사용하여 경고를 만들려면</span><span class="sxs-lookup"><span data-stu-id="2d251-134">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="2d251-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2d251-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2d251-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d251-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 <span data-ttu-id="2d251-138">자세한 내용은 [sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d251-138">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
