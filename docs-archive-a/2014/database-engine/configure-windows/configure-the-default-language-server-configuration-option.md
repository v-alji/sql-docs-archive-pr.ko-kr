---
title: default language 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b0e62fef112dad2c6c307946bc720adf1f14d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741252"
---
# <a name="configure-the-default-language-server-configuration-option"></a><span data-ttu-id="96ae7-102">default language 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="96ae7-102">Configure the default language Server Configuration Option</span></span>
  <span data-ttu-id="96ae7-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 기본 언어 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-103">This topic describes how to configure the **default language** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="96ae7-104">**기본 언어** 옵션을 사용하면 새로 만드는 모든 로그인의 기본 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-104">The **default language** option specifies the default language for all newly created logins.</span></span> <span data-ttu-id="96ae7-105">기본 언어를 설정하려면 원하는 언어의 **langid** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-105">To set default language, specify the **langid** value of the language you want.</span></span> <span data-ttu-id="96ae7-106">**sys.syslanguages** 호환성 뷰를 쿼리하여 **langid** 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-106">The **langid** value can be obtained by querying the **sys.syslanguages** compatibility view.</span></span>  
  
 <span data-ttu-id="96ae7-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="96ae7-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="96ae7-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="96ae7-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="96ae7-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="96ae7-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="96ae7-110">보안</span><span class="sxs-lookup"><span data-stu-id="96ae7-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="96ae7-111">**기본 언어 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="96ae7-111">**To configure the default language option, using:**</span></span>  
  
     [<span data-ttu-id="96ae7-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="96ae7-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="96ae7-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="96ae7-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="96ae7-114">**후속 작업:**  [기본 언어 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="96ae7-114">**Follow Up:**  [After you configure the default language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="96ae7-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="96ae7-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="96ae7-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="96ae7-116">Recommendations</span></span>  
  
-   <span data-ttu-id="96ae7-117">로그인의 기본 언어는 CREATE LOGIN 또는 ALTER LOGIN를 사용하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-117">The default language for a login can be overridden by using CREATE LOGIN or ALTER LOGIN.</span></span> <span data-ttu-id="96ae7-118">세션의 기본 언어는 ODBC(Open Database Connectivity) 또는 OLE DB API를 사용하여 각 세션 단위로 덮어쓰지 않는 한 해당 세션의 로그인 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-118">The default language for a session is the language for that session's login, unless overridden on a per-session basis by using the Open Database Connectivity (ODBC) or OLE DB APIs.</span></span> <span data-ttu-id="96ae7-119">**sys.syslanguages** 에서 정의한 언어 ID(0-32)에만 [기본 언어](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-119">Note that you can only set the **default language** option to a language ID defined in [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0-32).</span></span> <span data-ttu-id="96ae7-120">포함된 데이터베이스를 사용할 때는 CREATE DATABASE 또는 ALTER DATABASE를 사용하여 데이터베이스에 대해, 그리고 CREATE USER 또는 ALTER USER를 사용하여 포함된 데이터베이스 사용자에 대해 기본 언어를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-120">When you are using contained databases, a default language can be set for a database by using CREATE DATABASE or ALTER DATABASE, and for contained database users by using CREATE USER or ALTER USER.</span></span> <span data-ttu-id="96ae7-121">포함된 데이터베이스에서 기본 언어를 설정하면 **langid** 값, 언어 이름 또는 **sys.syslanguages**에 나열된 언어 별칭이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-121">Setting default languages in a contained database accepts **langid** value, the language name, or a language alias as listed in **sys.syslanguages**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="96ae7-122">보안</span><span class="sxs-lookup"><span data-stu-id="96ae7-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="96ae7-123">권한</span><span class="sxs-lookup"><span data-stu-id="96ae7-123">Permissions</span></span>  
 <span data-ttu-id="96ae7-124">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="96ae7-125">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="96ae7-126">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="96ae7-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="96ae7-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="96ae7-128">기본 언어 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="96ae7-128">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="96ae7-129">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="96ae7-130">**기타 서버 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="96ae7-131">**사용자의 기본 언어** 목록에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시스템 메시지를 표시하는 데 사용할 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-131">In the **Default language for users** box, choose the language in which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should display system messages.</span></span>  
  
     <span data-ttu-id="96ae7-132">기본 언어는 한국어(Korean)입니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-132">The default language is English.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="96ae7-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="96ae7-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="96ae7-134">기본 언어 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="96ae7-134">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="96ae7-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="96ae7-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="96ae7-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="96ae7-138">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `default language` 옵션을 프랑스어(`2`)로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `default language` option to French (`2`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 <span data-ttu-id="96ae7-139">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="96ae7-140">후속 작업: 기본 언어 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="96ae7-140">Follow Up: After you configure the default language option</span></span>  
 <span data-ttu-id="96ae7-141">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96ae7-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ae7-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96ae7-142">See Also</span></span>  
 <span data-ttu-id="96ae7-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-145">[CREATE USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-146">[ALTER USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-147">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-148">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-149">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96ae7-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="96ae7-150">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="96ae7-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="96ae7-151">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="96ae7-151">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
