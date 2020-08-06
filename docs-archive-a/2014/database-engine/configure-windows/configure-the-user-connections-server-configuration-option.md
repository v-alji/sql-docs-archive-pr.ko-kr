---
title: user connections 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- simultaneous connections [SQL Server]
- user connections option [SQL Server]
- users [SQL Server], simultaneous connections
- maximum number of simultaneous user connections
- connections [SQL Server], simultaneous
ms.assetid: 53beee6e-59fe-4276-9abb-8f1cec2a3508
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fbb4a17de131c128b5b1bb7cfb35a33b9d0037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646636"
---
# <a name="configure-the-user-connections-server-configuration-option"></a><span data-ttu-id="543e1-102">user connections 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="543e1-102">Configure the user connections Server Configuration Option</span></span>
  <span data-ttu-id="543e1-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 사용자 연결 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-103">This topic describes how to set the **user connections** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="543e1-104">**사용자 연결** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 허용되는 최대 동시 사용자 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-104">The **user connections** option specifies the maximum number of simultaneous user connections that are allowed on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="543e1-105">허용되는 실제 사용자 연결 수는 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전과 애플리케이션 및 하드웨어 제한에 따라서도 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-105">The actual number of user connections allowed also depends on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using, and also the limits of your application or applications and hardware.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="543e1-106">는 사용자 연결을 최대 32,767개까지 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-106">allows a maximum of 32,767 user connections.</span></span> <span data-ttu-id="543e1-107">**사용자 연결 수** 는 동적(자체 구성) 옵션이므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 허용 가능한 최대값까지 필요한 만큼 자동으로 최대 사용자 연결 수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-107">Because **user connections** is a dynamic (self-configuring) option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adjusts the maximum number of user connections automatically as needed, up to the maximum value allowable.</span></span> <span data-ttu-id="543e1-108">예를 들어, 10명의 사용자만 로그인했으면 10개의 사용자 연결 개체가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-108">For example, if only 10 users are logged in, 10 user connection objects are allocated.</span></span> <span data-ttu-id="543e1-109">대부분의 경우 이 옵션의 값을 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-109">In most cases, you do not have to change the value for this option.</span></span> <span data-ttu-id="543e1-110">기본값은 0이며 최대(32,767) 사용자 연결을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-110">The default is 0, which means that the maximum (32,767) user connections are allowed.</span></span>  
  
 <span data-ttu-id="543e1-111">시스템에 허용되는 최대 사용자 연결 수를 확인하려면 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 실행하거나 [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-111">To determine the maximum number of user connections that your system allows, you can execute [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) or query the [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="543e1-112">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="543e1-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="543e1-113">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="543e1-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="543e1-114">권장 사항</span><span class="sxs-lookup"><span data-stu-id="543e1-114">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="543e1-115">보안</span><span class="sxs-lookup"><span data-stu-id="543e1-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="543e1-116">**사용자 연결 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="543e1-116">**To configure the user connections option, using:**</span></span>  
  
     [<span data-ttu-id="543e1-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="543e1-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="543e1-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="543e1-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="543e1-119">**후속 작업:**  [사용자 연결 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="543e1-119">**Follow Up:**  [After you configure the user connections option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="543e1-120">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="543e1-120">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="543e1-121">권장 사항</span><span class="sxs-lookup"><span data-stu-id="543e1-121">Recommendations</span></span>  
  
-   <span data-ttu-id="543e1-122">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="543e1-123">**사용자 연결** 옵션을 사용하면 동시 연결이 너무 많아 서버가 과부하되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-123">Using the **user connections** option helps avoid overloading the server with too many concurrent connections.</span></span> <span data-ttu-id="543e1-124">시스템과 사용자 요구 사항에 따라 연결 수를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-124">You can estimate the number of connections based on system and user requirements.</span></span> <span data-ttu-id="543e1-125">예를 들어, 사용자가 많은 시스템에서는 각 사용자가 고유하게 연결할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-125">For example, on a system with many users, each user would not usually require a unique connection.</span></span> <span data-ttu-id="543e1-126">여러 사용자 간에 연결을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-126">Connections can be shared among users.</span></span> <span data-ttu-id="543e1-127">OLE DB 애플리케이션을 실행 중인 사용자는 각 열린 연결 개체당 하나의 연결이 필요하며 ODBC 애플리케이션을 실행 중인 사용자는 애플리케이션에 있는 각 활성 연결 핸들당 하나의 연결이 필요합니다. 또한 DB-Library 애플리케이션을 실행 중인 사용자는 DB-Library **dbopen** 함수를 호출하는 시작된 각 프로세스당 하나의 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-127">Users running OLE DB applications need a connection for each open connection object, users running Open Database Connectivity (ODBC) applications need a connection for each active connection handle in the application, and users running DB-Library applications need one connection for each process started that calls the DB-Library **dbopen** function.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="543e1-128">이 옵션을 사용해야 하는 경우 연결의 사용 여부에 관계없이 각 연결에 오버헤드가 필요하므로 값을 너무 높게 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="543e1-128">If you must use this option, do not set the value too high, because each connection has overhead regardless of whether the connection is being used.</span></span> <span data-ttu-id="543e1-129">최대 사용자 연결 수를 초과하면 오류 메시지가 나타나고 다른 연결을 사용할 수 있게 될 때까지 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-129">If you exceed the maximum number of user connections, you receive an error message and are not able to connect until another connection becomes available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="543e1-130">보안</span><span class="sxs-lookup"><span data-stu-id="543e1-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="543e1-131">권한</span><span class="sxs-lookup"><span data-stu-id="543e1-131">Permissions</span></span>  
 <span data-ttu-id="543e1-132">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="543e1-133">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="543e1-134">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="543e1-135">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="543e1-135">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="543e1-136">사용자 연결 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="543e1-136">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="543e1-137">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-137">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="543e1-138">**연결** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-138">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="543e1-139">**연결**의 **최대 동시 연결 수** 상자에 0부터 32767까지의 값을 입력하거나 선택하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 동시에 연결할 수 있는 최대 사용자 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-139">Under **Connections**, in the **Max number of concurrent connections** box, type or select a value from 0 through 32767 to set the maximum number of users that are allowed to connect simultaneously to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="543e1-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-140">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="543e1-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="543e1-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="543e1-142">사용자 연결 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="543e1-142">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="543e1-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="543e1-144">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="543e1-145">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="543e1-146">다음 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `user connections` 옵션 값을 `325` 명의 사용자로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the value of the `user connections` option to `325` users.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'user connections', 325 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="543e1-147">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-user-connections-option"></a><a name="FollowUp"></a> <span data-ttu-id="543e1-148">후속 작업: 사용자 연결 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="543e1-148">Follow Up: After you configure the user connections option</span></span>  
 <span data-ttu-id="543e1-149">설정을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="543e1-149">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543e1-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="543e1-150">See Also</span></span>  
 <span data-ttu-id="543e1-151">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="543e1-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="543e1-152">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="543e1-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="543e1-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="543e1-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
