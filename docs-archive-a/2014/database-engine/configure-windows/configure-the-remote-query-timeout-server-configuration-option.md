---
title: remote query timeout 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 74f82d621d7f0375a6a3ca604abba00f83fc6024
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740431"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a><span data-ttu-id="cce12-102">remote query timeout 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="cce12-102">Configure the remote query timeout Server Configuration Option</span></span>
  <span data-ttu-id="cce12-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 원격 쿼리 제한 시간 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-103">This topic describes how to configure the **remote query timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cce12-104">**원격 쿼리 제한 시간** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 제한 시간이 초과될 때까지 원격 작업을 수행할 수 있는 시간(초)을 지정합니다. 이 옵션의 기본값은 600이며, 10분 동안 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-104">The **remote query timeout** option specifies how long, in seconds, a remote operation can take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default value for this option is 600, which allows a 10-minute wait.</span></span> <span data-ttu-id="cce12-105">이 값은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 시작된 나가는 연결에 원격 쿼리로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-105">This value applies to an outgoing connection initiated by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] as a remote query.</span></span> <span data-ttu-id="cce12-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 수신된 쿼리에는 이 값이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-106">This value has no effect on queries received by the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="cce12-107">제한 시간을 사용하지 않으려면 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-107">To disable the time-out, set the value to 0.</span></span> <span data-ttu-id="cce12-108">쿼리는 완료될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-108">A query will wait until it completes.</span></span>  
  
 <span data-ttu-id="cce12-109">유형이 다른 쿼리의 경우 **원격 쿼리 제한 시간** 은 DBPROP_COMMANDTIMEOUT 행 집합 속성을 사용하여 명령 개체에서 초기화한 쿼리 시간이 초과되기 전에 원격 공급자가 결과 집합을 기다리는 시간(초)을 지정합니다. 이 값은 또한 원격 공급자에서 지원하는 경우 DBPROP_GENERALTIMEOUT을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-109">For heterogeneous queries, **remote query timeout** specifies the number of seconds (initialized in the command object using the DBPROP_COMMANDTIMEOUT rowset property) that a remote provider should wait for result sets before the query times out. This value is also used to set DBPROP_GENERALTIMEOUT if supported by the remote provider.</span></span> <span data-ttu-id="cce12-110">이로 인해 지정한 시간이 지난 다음 다른 작업의 시간이 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-110">This will cause any other operations to time out after the specified number of seconds.</span></span>  
  
 <span data-ttu-id="cce12-111">원격 저장 프로시저의 경우 **원격 쿼리 제한 시간** 은 원격 `EXEC` 문을 전달한 다음 원격 저장 프로시저 시간이 초과되기 전까지의 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-111">For remote stored procedures, **remote query timeout** specifies the number of seconds that must elapse after sending a remote `EXEC` statement before the remote stored procedure times out.</span></span>  
  
 <span data-ttu-id="cce12-112">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cce12-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cce12-113">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cce12-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cce12-114">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cce12-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="cce12-115">보안</span><span class="sxs-lookup"><span data-stu-id="cce12-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cce12-116">**원격 쿼리 제한 시간 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="cce12-116">**To configure the remote query timeout option, using:**</span></span>  
  
     [<span data-ttu-id="cce12-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cce12-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cce12-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cce12-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="cce12-119">**후속 작업:**  [원격 쿼리 제한 시간 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cce12-119">**Follow Up:**  [After you configure the remote query timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cce12-120">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cce12-120">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="cce12-121">필수 조건</span><span class="sxs-lookup"><span data-stu-id="cce12-121">Prerequisites</span></span>  
  
-   <span data-ttu-id="cce12-122">이 값을 설정하려면 먼저 원격 서버 연결이 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-122">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cce12-123">보안</span><span class="sxs-lookup"><span data-stu-id="cce12-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cce12-124">권한</span><span class="sxs-lookup"><span data-stu-id="cce12-124">Permissions</span></span>  
 <span data-ttu-id="cce12-125">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-125">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="cce12-126">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-126">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="cce12-127">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cce12-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cce12-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="cce12-129">원격 쿼리 제한 시간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="cce12-129">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="cce12-130">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-130">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="cce12-131">**연결** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-131">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="cce12-132">**원격 서버 연결**의 **원격 쿼리 제한 시간** 상자에 0부터 2,147,483,647 사이의 값을 입력하거나 선택하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 제한 시간이 초과되기 전까지 대기할 최대 시간(초)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-132">Under **Remote server connections**, in the **Remote query timeout** box, type or select a value from 0 through 2,147,483,647 to set the maximum number seconds for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to wait before timing out.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cce12-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cce12-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="cce12-134">원격 쿼리 제한 시간 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="cce12-134">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="cce12-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cce12-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cce12-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cce12-138">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 통해 `remote query timeout` 옵션 값을 `0` 으로 설정하여 제한 시간을 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote query timeout` option to `0` to disable the time-out.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="cce12-139">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-query-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="cce12-140">후속 작업: 원격 쿼리 제한 시간 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="cce12-140">Follow Up: After you configure the remote query timeout option</span></span>  
 <span data-ttu-id="cce12-141">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cce12-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce12-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cce12-142">See Also</span></span>  
 <span data-ttu-id="cce12-143">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cce12-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="cce12-144">[행 집합 속성 및 동작](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="cce12-144">[Rowset Properties and Behaviors](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 <span data-ttu-id="cce12-145">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cce12-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="cce12-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cce12-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
