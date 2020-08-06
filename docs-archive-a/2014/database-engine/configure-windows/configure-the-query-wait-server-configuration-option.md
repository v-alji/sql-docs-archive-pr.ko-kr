---
title: query wait 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], timing out
- time [SQL Server], query wait time
- query wait option [SQL Server]
ms.assetid: 0fc4aa01-65a3-4a33-9ef4-caca41add238
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 638afff2aa05a9fc4e61bc71e8610dba1dda8cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652331"
---
# <a name="configure-the-query-wait-server-configuration-option"></a><span data-ttu-id="80711-102">query wait 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="80711-102">Configure the query wait Server Configuration Option</span></span>
  <span data-ttu-id="80711-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 쿼리 대기 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-103">This topic describes how to configure the **query wait** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="80711-104">정렬이나 해시처럼 메모리를 많이 사용하는 쿼리를 실행하면 실행에 필요한 충분한 메모리가 확보될 때까지 쿼리가 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="80711-104">Memory-intensive queries (such as those involving sorting and hashing) are queued when there is not enough memory available to run the query.</span></span> <span data-ttu-id="80711-105">**쿼리 대기** 옵션은 리소스에 대한 쿼리의 최대 대기 제한 시간을 초 단위(0 - 2147483647)로 지정합니다. 이 옵션의 기본값은 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="80711-105">The **query wait** option specifies the time, in seconds (from 0 through 2147483647), that a query waits for resources before it times out. The default value for this option is -1.</span></span> <span data-ttu-id="80711-106">즉, 제한 시간이 예상 쿼리 비용의 25배로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="80711-106">This means the time-out is calculated as 25 times the estimated query cost.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80711-107">대기 중인 쿼리를 포함하는 트랜잭션은 쿼리가 메모리를 기다리는 동안 잠금을 유지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80711-107">A transaction that contains the waiting query might hold locks while the query waits for memory.</span></span> <span data-ttu-id="80711-108">드물지만 검색할 수 없는 교착 상태가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80711-108">In rare situations, it is possible for an undetectable deadlock to occur.</span></span> <span data-ttu-id="80711-109">쿼리 대기 시간을 줄이면 이런 교착 상태의 가능성을 낮출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80711-109">Decreasing the query wait time lowers the probability of such deadlocks.</span></span> <span data-ttu-id="80711-110">결국 기다리는 쿼리는 종료되고 트랜잭션 잠금은 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="80711-110">Eventually, a waiting query will be terminated and the transaction locks released.</span></span> <span data-ttu-id="80711-111">그러나 최대 대기 시간을 늘리면 쿼리가 종료되는 시간이 길어질 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="80711-111">However, increasing the maximum wait time may increase the amount of time for the query to be terminated.</span></span> <span data-ttu-id="80711-112">이 옵션은 변경하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="80711-112">Changes to this option are not recommended.</span></span>  
  
 <span data-ttu-id="80711-113">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="80711-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="80711-114">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="80711-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="80711-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="80711-115">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="80711-116">보안</span><span class="sxs-lookup"><span data-stu-id="80711-116">Security</span></span>](#Security)  
  
-   <span data-ttu-id="80711-117">**쿼리 대기 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="80711-117">**To configure the query wait option, using:**</span></span>  
  
     [<span data-ttu-id="80711-118">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="80711-118">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="80711-119">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="80711-119">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="80711-120">**후속 작업:**  [쿼리 대기 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="80711-120">**Follow Up:**  [After you configure the query wait option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="80711-121">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="80711-121">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="80711-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="80711-122">Recommendations</span></span>  
  
-   <span data-ttu-id="80711-123">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="80711-124">보안</span><span class="sxs-lookup"><span data-stu-id="80711-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="80711-125">권한</span><span class="sxs-lookup"><span data-stu-id="80711-125">Permissions</span></span>  
 <span data-ttu-id="80711-126">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="80711-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="80711-127">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="80711-128">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80711-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="80711-129">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="80711-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="80711-130">쿼리 대기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="80711-130">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="80711-131">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="80711-132">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-132">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="80711-133">**병렬 처리**에서 **쿼리 대기** 옵션에 알맞은 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-133">Under **Parallelism**, type the desired value for the **query wait** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="80711-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="80711-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="80711-135">쿼리 대기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="80711-135">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="80711-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="80711-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="80711-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="80711-139">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `query wait` 옵션 값을 `7500` 초로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="80711-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query wait` option to `7500` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query wait', 7500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="80711-140">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80711-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-wait-option"></a><a name="FollowUp"></a> <span data-ttu-id="80711-141">후속 작업: 쿼리 대기 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="80711-141">Follow Up: After you configure the query wait option</span></span>  
 <span data-ttu-id="80711-142">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80711-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80711-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80711-143">See Also</span></span>  
 <span data-ttu-id="80711-144">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="80711-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="80711-145">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80711-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="80711-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80711-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
