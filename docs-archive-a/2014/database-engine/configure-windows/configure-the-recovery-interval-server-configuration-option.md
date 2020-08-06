---
title: recovery interval 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 560d514ba8dd1503b59b3b59ecf404d876e24cd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647234"
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a><span data-ttu-id="cf9c7-102">recovery interval 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="cf9c7-102">Configure the recovery interval Server Configuration Option</span></span>
  <span data-ttu-id="cf9c7-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 복구 간격 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-103">This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cf9c7-104">**복구 간격** 옵션은 데이터베이스를 복구하는 데 필요한 시간의 상한값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-104">The **recovery interval** option defines an upper limit on the time recovering a database should take.</span></span> <span data-ttu-id="cf9c7-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서는 이 옵션에 지정된 값을 사용하여 지정된 데이터베이스에 대해 [자동 검사점](../../relational-databases/logs/database-checkpoints-sql-server.md) 을 실행하는 대략적인 빈도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-105">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../../relational-databases/logs/database-checkpoints-sql-server.md) to issue automatic checkpoints on a given database.</span></span>  
  
 <span data-ttu-id="cf9c7-106">기본 복구 간격 값은 0이며 이는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 복구 간격을 자동으로 구성함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-106">The default recovery-interval value is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to automatically configure the recovery interval.</span></span> <span data-ttu-id="cf9c7-107">일반적으로 기본 복구 간격을 사용하면 활성 데이터베이스의 경우 자동 검사점의 실행 간격은 약 1분이고 복구 시간은 1분 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-107">Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute.</span></span> <span data-ttu-id="cf9c7-108">값이 높을수록 최대 복구 시간(분)의 근사치가 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-108">Higher values indicate the approximate maximum recovery time, in minutes.</span></span> <span data-ttu-id="cf9c7-109">예를 들어 복구 간격으로 3을 설정하면 최대 복구 시간이 약 3분이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-109">For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.</span></span>  
  
 <span data-ttu-id="cf9c7-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cf9c7-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cf9c7-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cf9c7-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cf9c7-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="cf9c7-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cf9c7-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="cf9c7-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="cf9c7-114">보안</span><span class="sxs-lookup"><span data-stu-id="cf9c7-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cf9c7-115">**다음을 사용하여 복구 간격 서버 구성 옵션을 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="cf9c7-115">**To Configure the recovery interval Server Configuration Option, using:**</span></span>  
  
     [<span data-ttu-id="cf9c7-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf9c7-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cf9c7-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf9c7-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="cf9c7-118">**후속 작업:**  [복구 간격 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cf9c7-118">**Follow Up:**  [After you configure the recovery interval option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf9c7-119">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cf9c7-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cf9c7-120">제한 사항</span><span class="sxs-lookup"><span data-stu-id="cf9c7-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cf9c7-121">복구 간격은 기본 대상 복구 시간(0)을 사용하는 데이터베이스에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-121">The recovery interval affects only databases that use the default target recovery time (0).</span></span> <span data-ttu-id="cf9c7-122">데이터베이스에 대한 서버 복구 간격을 재정의하려면 데이터베이스에 기본이 아닌 대상 복구 시간을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-122">To override the server recovery interval on a database, configure a non-default target recovery time on the database.</span></span> <span data-ttu-id="cf9c7-123">자세한 내용은 [데이터베이스의 대상 복구 시간 변경&#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-123">For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cf9c7-124">권장 사항</span><span class="sxs-lookup"><span data-stu-id="cf9c7-124">Recommendations</span></span>  
  
-   <span data-ttu-id="cf9c7-125">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-125">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="cf9c7-126">일반적으로 성능 문제가 없는 한 복구 간격을 0으로 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-126">Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems.</span></span> <span data-ttu-id="cf9c7-127">복구 간격 설정을 늘리려는 경우에는 값을 조금씩 늘려가며 그에 따라 복구 성능에 미치는 영향을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-127">If you decide to increase the recovery-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.</span></span>  
  
-   <span data-ttu-id="cf9c7-128">**sp_configure** 를 사용하여 **복구 간격** 옵션 값을 60분 이상으로 변경하는 경우 RECONFIGURE WITH OVERRIDE를 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-128">If you use **sp_configure** to change the value of the **recovery interval** option to more than 60 (minutes), specify RECONFIGURE WITH OVERRIDE.</span></span> <span data-ttu-id="cf9c7-129">WITH OVERRIDE를 지정하면 유효하지 않은 값 또는 권장되지 않는 값이 있는지 확인하는 구성 값 검사가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-129">WITH OVERRIDE disables configuration value checking (for values that are not valid or are nonrecommended values).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf9c7-130">보안</span><span class="sxs-lookup"><span data-stu-id="cf9c7-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf9c7-131">권한</span><span class="sxs-lookup"><span data-stu-id="cf9c7-131">Permissions</span></span>  
 <span data-ttu-id="cf9c7-132">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="cf9c7-133">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="cf9c7-134">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf9c7-135">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cf9c7-135">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cf9c7-136">**복구 간격을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="cf9c7-136">**To set the recovery interval**</span></span>  
  
1.  <span data-ttu-id="cf9c7-137">개체 탐색기에서 서버 인스턴스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-137">In Object Explorer, right-click server instance and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="cf9c7-138">**데이터베이스 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-138">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="cf9c7-139">**복구**의 **복구 간격(분)** 입력란에 0부터 32767까지 범위의 값을 입력하거나 선택하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시작 시 각 데이터베이스를 복구하는 데 걸리는 최대 시간을 분으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-139">Under **Recovery**, in the **Recovery interval (minutes)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should spend recovering each database at startup.</span></span> <span data-ttu-id="cf9c7-140">기본값 0을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 자동으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-140">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf9c7-141">기본값을 설정하면 실제 운영 시 1분 이하의 복구 시간이 사용되고 활성 데이터베이스의 경우 약 1분 간격으로 검사점이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-141">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cf9c7-142">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cf9c7-142">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-recovery-interval"></a><span data-ttu-id="cf9c7-143">복구 간격을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cf9c7-143">To set the recovery interval</span></span>  
  
1.  <span data-ttu-id="cf9c7-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf9c7-145">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf9c7-146">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cf9c7-147">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `recovery interval` 옵션 값을 `3` 분으로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `recovery interval` option to `3` minutes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="cf9c7-148">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-recovery-internal-option"></a><a name="FollowUp"></a> <span data-ttu-id="cf9c7-149">후속 작업: recovery internal 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="cf9c7-149">Follow Up: After you configure the recovery internal option</span></span>  
 <span data-ttu-id="cf9c7-150">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9c7-150">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9c7-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf9c7-151">See Also</span></span>  
 <span data-ttu-id="cf9c7-152">[데이터베이스의 대상 복구 시간 변경&#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf9c7-152">[Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span></span>  
 <span data-ttu-id="cf9c7-153">[데이터베이스 검사점&#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf9c7-153">[Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span></span>  
 <span data-ttu-id="cf9c7-154">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf9c7-154">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="cf9c7-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cf9c7-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="cf9c7-156">[show advanced options 서버 구성 옵션](show-advanced-options-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="cf9c7-156">[show advanced options Server Configuration Option](show-advanced-options-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="cf9c7-157">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cf9c7-157">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
