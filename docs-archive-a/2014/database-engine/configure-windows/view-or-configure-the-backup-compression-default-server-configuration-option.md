---
title: backup compression default 서버 구성 옵션 보기 또는 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], backup compression default option
- backup compression [SQL Server], backup compression default Option
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02458c069d7c155b199e24feb7ef028ae0f258a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661341"
---
# <a name="view-or-configure-the-backup-compression-default-server-configuration-option"></a><span data-ttu-id="0f2ee-102">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="0f2ee-102">View or Configure the backup compression default Server Configuration Option</span></span>
  <span data-ttu-id="0f2ee-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 백업 압축 기본값 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-103">This topic describes how to view or configure the **backup compression default** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0f2ee-104">**백업 압축 기본값** 옵션은 서버 인스턴스가 기본적으로 압축된 백업을 만드는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-104">The **backup compression default** option determines whether the server instance creates compressed backups by default.</span></span> <span data-ttu-id="0f2ee-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이(가) 설치되면 **백업 압축 기본값** 옵션이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-105">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, the **backup compression default** option is off.</span></span>  
  
 <span data-ttu-id="0f2ee-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0f2ee-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0f2ee-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0f2ee-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0f2ee-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0f2ee-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0f2ee-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="0f2ee-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0f2ee-110">보안</span><span class="sxs-lookup"><span data-stu-id="0f2ee-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0f2ee-111">**백업 압축 기본값 옵션을 보거나 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="0f2ee-111">**To view or configure the backup compression default option, using:**</span></span>  
  
     [<span data-ttu-id="0f2ee-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0f2ee-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0f2ee-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0f2ee-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0f2ee-114">**후속 작업:**  [백업 압축 기본값 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0f2ee-114">**Follow Up:**  [After you configure the backup compression default option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0f2ee-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0f2ee-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0f2ee-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0f2ee-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0f2ee-117">일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 백업 압축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-117">Backup compression is not available in all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0f2ee-118">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-118">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="0f2ee-119">기본적으로 압축하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-119">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="0f2ee-120">따라서 CPU 사용량이 [리소스 관리자](../../relational-databases/resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-120">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="0f2ee-121">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-121">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0f2ee-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="0f2ee-122">Recommendations</span></span>  
  
-   <span data-ttu-id="0f2ee-123">개별 백업을 만들거나 로그 전달을 구성하거나 유지 관리 계획을 만들 때 서버 수준 기본값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-123">When you are creating an individual backup, configuring a log shipping configuration, or creating a maintenance plan, you can override the server-level default.</span></span>  
  
-   <span data-ttu-id="0f2ee-124">백업 압축은 디스크 백업 디바이스와 테이프 백업 디바이스 모두에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-124">Backup compression is supported for both disk backup devices and tape backup devices.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0f2ee-125">보안</span><span class="sxs-lookup"><span data-stu-id="0f2ee-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0f2ee-126">권한</span><span class="sxs-lookup"><span data-stu-id="0f2ee-126">Permissions</span></span>  
 <span data-ttu-id="0f2ee-127">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-127">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="0f2ee-128">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-128">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="0f2ee-129">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-129">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0f2ee-130">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0f2ee-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-the-backup-compression-default-option"></a><span data-ttu-id="0f2ee-131">백업 압축 기본값 옵션을 보거나 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0f2ee-131">To view or configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="0f2ee-132">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-132">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0f2ee-133">**데이터베이스 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-133">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="0f2ee-134">**백업 및 복원**아래의 **백업 압축** 에 **백업 압축 기본값** 옵션의 현재 설정이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-134">Under **Backup and restore**, **Compress backup** shows the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="0f2ee-135">이 설정은 다음과 같이 백업 압축의 서버 수준 기본값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-135">This setting determines the server-level default for compressing backups, as follows:</span></span>  
  
    -   <span data-ttu-id="0f2ee-136">**백업 압축** 상자가 비어 있으면 새 백업은 기본적으로 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-136">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
    -   <span data-ttu-id="0f2ee-137">**백업 압축** 상자가 선택되어 있으면 새 백업은 기본적으로 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-137">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
     <span data-ttu-id="0f2ee-138">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버인 경우 **백업 압축** 상자를 클릭하여 기본 설정을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-138">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can also change the default setting by clicking the **Compress backup** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0f2ee-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0f2ee-139">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-backup-compression-default-option"></a><span data-ttu-id="0f2ee-140">백업 압축 기본값 옵션을 보려면</span><span class="sxs-lookup"><span data-stu-id="0f2ee-140">To view the backup compression default option</span></span>  
  
1.  <span data-ttu-id="0f2ee-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0f2ee-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0f2ee-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0f2ee-144">다음 예에서는 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 카탈로그 뷰를 쿼리하여 `backup compression default`의 값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-144">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to determine the value for `backup compression default`.</span></span> <span data-ttu-id="0f2ee-145">값이 0이면 백업 압축이 사용되지 않고, 값이 1이면 백업 압축이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-145">A value of 0 means that backup compression is off, and a value of 1 means that backup compression is enabled.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
  
```  
  
#### <a name="to-configure-the-backup-compression-default-option"></a><span data-ttu-id="0f2ee-146">백업 압축 기본값 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0f2ee-146">To configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="0f2ee-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0f2ee-148">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0f2ee-149">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0f2ee-150">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 기본적으로 압축된 백업을 만들도록 서버 인스턴스를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the server instance to create compressed backups by default.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO  
  
```  
  
 <span data-ttu-id="0f2ee-151">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-backup-compression-default-option"></a><a name="FollowUp"></a> <span data-ttu-id="0f2ee-152">후속 작업: 백업 압축 기본값 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="0f2ee-152">Follow Up: After you configure the backup compression default option</span></span>  
 <span data-ttu-id="0f2ee-153">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f2ee-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2ee-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f2ee-154">See Also</span></span>  
 <span data-ttu-id="0f2ee-155">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0f2ee-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0f2ee-156">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0f2ee-156">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="0f2ee-157">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0f2ee-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0f2ee-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0f2ee-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="0f2ee-159">백업 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0f2ee-159">Backup Overview &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  
