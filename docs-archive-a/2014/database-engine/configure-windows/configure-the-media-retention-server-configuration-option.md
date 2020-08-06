---
title: media retention 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 092e0a2b5cfc30fd2d2362645fc1242bf4a1651e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649173"
---
# <a name="configure-the-media-retention-server-configuration-option"></a><span data-ttu-id="a68de-102">media retention 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="a68de-102">Configure the media retention Server Configuration Option</span></span>
  <span data-ttu-id="a68de-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 미디어 보존 기간 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-103">This topic describes how to configure the **media retention** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a68de-104">**미디어 보존 기간** 옵션을 사용하여 각 백업 세트를 보존하는 기간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-104">The **media retention** option specifies the length of time to retain each backup set.</span></span> <span data-ttu-id="a68de-105">이 옵션을 통해 지정된 일수가 경과하기 전에 백업을 덮어쓰지 않도록 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-105">The option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span> <span data-ttu-id="a68de-106">**미디어 보존 기간** 옵션을 구성한 후 백업을 수행할 때마다 시스템 백업을 보존할 기간을 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-106">After you configure **media retention** option, you do not have to specify the length of time to retain system backups each time you perform a backup.</span></span> <span data-ttu-id="a68de-107">기본값은 0일이고, 최대값은 365일입니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-107">The default value is 0 days, and the maximum value is 365 days.</span></span>  
  
 <span data-ttu-id="a68de-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a68de-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a68de-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a68de-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a68de-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a68de-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a68de-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a68de-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a68de-112">보안</span><span class="sxs-lookup"><span data-stu-id="a68de-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a68de-113">**미디어 보존 기간 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="a68de-113">**To configure the media retention option, using:**</span></span>  
  
     [<span data-ttu-id="a68de-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a68de-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a68de-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a68de-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a68de-116">**후속 작업:**  [미디어 보존 기간 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a68de-116">**Follow Up:**  [After you configure the media retention option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a68de-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a68de-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a68de-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a68de-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a68de-119">설정된 기간이 지나기 전에 백업 미디어를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 경고 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-119">If you use the backup medium before the set number of days has passed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] issues a warning message.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a68de-120">에 경고가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-120">does not issue a warning unless you change the default.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a68de-121">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a68de-121">Recommendations</span></span>  
  
-   <span data-ttu-id="a68de-122">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="a68de-123">**미디어 보존 기간** 옵션은 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문의 RETAINDAYS 절을 사용하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-123">The **media retention** option can be overridden by using the RETAINDAYS clause of the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a68de-124">보안</span><span class="sxs-lookup"><span data-stu-id="a68de-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a68de-125">권한</span><span class="sxs-lookup"><span data-stu-id="a68de-125">Permissions</span></span>  
 <span data-ttu-id="a68de-126">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a68de-127">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a68de-128">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a68de-129">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a68de-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="a68de-130">미디어 보존 기간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a68de-130">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="a68de-131">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a68de-132">**데이터베이스 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-132">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="a68de-133">**백업/복원**의 **백업 미디어 기본 보존 기간** 상자에서 0부터 365까지의 값을 입력하거나 선택하여 데이터베이스나 트랜잭션 로그 백업 후 백업 미디어가 보존될 일수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-133">Under **Backup/Restore**, in the **Default backup media retention** box, type or select a value from 0 through 365 to set the number of days the backup medium will be retained after a database or transaction log backup.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a68de-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a68de-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="a68de-135">미디어 보존 기간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a68de-135">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="a68de-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a68de-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a68de-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a68de-139">다음 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `media retention` 옵션의 값을 `60` 일로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `media retention` option to `60` days.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="a68de-140">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-media-retention-option"></a><a name="FollowUp"></a> <span data-ttu-id="a68de-141">후속 작업: 미디어 보존 기간 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="a68de-141">Follow Up: After you configure the media retention option</span></span>  
 <span data-ttu-id="a68de-142">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a68de-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68de-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a68de-143">See Also</span></span>  
 <span data-ttu-id="a68de-144">[SQL Server 데이터베이스 백업 및 복원](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a68de-144">[Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="a68de-145">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a68de-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a68de-146">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a68de-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a68de-147">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a68de-147">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="a68de-148">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a68de-148">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
