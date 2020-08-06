---
title: query governor cost limit 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4f8420bf8ed8c08d3626c797968c041a40f7c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647235"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a><span data-ttu-id="9beaa-102">query governor cost limit 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="9beaa-102">Configure the query governor cost limit Server Configuration Option</span></span>
  <span data-ttu-id="9beaa-103">이 항목에서는 또는을 사용 하 `query governor cost limit` 여에서 서버 구성 옵션을 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9beaa-103">This topic describes how to configure the `query governor cost limit` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9beaa-104">쿼리 관리자 비용 제한 옵션은 쿼리 실행 제한 시간에 대한 상한값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-104">The query governor cost limit option specifies an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="9beaa-105">쿼리 비용이란 특정 하드웨어 구성에서 쿼리를 완료하는 데 필요한 예상 소요 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-105">Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="9beaa-106">이 옵션의 기본값은 0이며, 이 값은 쿼리 관리자 설정을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-106">The default value for this option is 0, which sets the query governor to off.</span></span> <span data-ttu-id="9beaa-107">기본값을 사용하면 시간 제한 없이 모든 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-107">This allows all queries to run without any time limitation.</span></span> <span data-ttu-id="9beaa-108">0이나 음수가 아닌 값을 지정하면 쿼리 관리자가 그 값을 초과하는 예상 비용을 갖는 쿼리의 실행을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-108">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.</span></span>  
  
 <span data-ttu-id="9beaa-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9beaa-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9beaa-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9beaa-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9beaa-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9beaa-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9beaa-112">보안</span><span class="sxs-lookup"><span data-stu-id="9beaa-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9beaa-113">**쿼리 관리자 비용 제한 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="9beaa-113">**To configure the query governor cost limit option, using:**</span></span>  
  
     [<span data-ttu-id="9beaa-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9beaa-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9beaa-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9beaa-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="9beaa-116">**후속 작업:**  [쿼리 관리자 비용 제한 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9beaa-116">**Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9beaa-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9beaa-117">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9beaa-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9beaa-118">Recommendations</span></span>  
  
-   <span data-ttu-id="9beaa-119">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-119">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="9beaa-120">각 연결에 대한 쿼리 관리자 비용 제한 값을 변경하려면 [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) 문을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9beaa-120">To change the value query governor cost limit on a per-connection basis, use the [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9beaa-121">보안</span><span class="sxs-lookup"><span data-stu-id="9beaa-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9beaa-122">권한</span><span class="sxs-lookup"><span data-stu-id="9beaa-122">Permissions</span></span>  
 <span data-ttu-id="9beaa-123">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-123">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="9beaa-124">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-124">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="9beaa-125">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-125">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9beaa-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9beaa-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="9beaa-127">쿼리 관리자 비용 제한 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9beaa-127">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="9beaa-128">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-128">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9beaa-129">**연결** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-129">Click the **Connections** page.</span></span>  
  
3.  <span data-ttu-id="9beaa-130">**쿼리 관리자를 사용하여 장기 실행 쿼리 방지** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-130">Select or clear the **Use query governor to prevent long-running queries** check box.</span></span>  
  
     <span data-ttu-id="9beaa-131">이 확인란을 선택하는 경우 아래 입력란에 양수 값을 입력합니다. 쿼리 관리자는 이 값을 사용하여 실행 길이가 이 값을 초과하는 쿼리는 실행할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-131">If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9beaa-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9beaa-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="9beaa-133">쿼리 관리자 비용 제한 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9beaa-133">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="9beaa-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9beaa-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9beaa-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9beaa-137">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `query governor cost limit` 옵션 값을 `120` 초로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query governor cost limit` option to `120` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="9beaa-138">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-governor-cost-limit-option"></a><a name="FollowUp"></a> <span data-ttu-id="9beaa-139">후속 작업: 쿼리 관리자 비용 제한 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="9beaa-139">Follow Up: After you configure the query governor cost limit option</span></span>  
 <span data-ttu-id="9beaa-140">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9beaa-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9beaa-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9beaa-141">See Also</span></span>  
 <span data-ttu-id="9beaa-142">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9beaa-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="9beaa-143">[SET QUERY_GOVERNOR_COST_LIMIT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9beaa-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span></span>  
 <span data-ttu-id="9beaa-144">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9beaa-144">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="9beaa-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9beaa-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
