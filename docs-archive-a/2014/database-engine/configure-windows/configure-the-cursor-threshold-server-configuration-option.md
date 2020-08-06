---
title: cursor threshold 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d7fd9ecafda270a02f1fba9f5dd74adc9e299d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661356"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a><span data-ttu-id="1443c-102">cursor threshold 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="1443c-102">Configure the cursor threshold Server Configuration Option</span></span>
  <span data-ttu-id="1443c-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 커서 임계값 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-103">This topic describes how to configure the **cursor threshold** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1443c-104">**커서 임계값** 옵션은 커서 키 집합이 비동기적으로 생성되는 커서 집합의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-104">The **cursor threshold** option specifies the number of rows in the cursor set at which cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="1443c-105">커서에서 결과 집합에 대해 키 집합을 생성할 때 쿼리 최적화 프로그램은 해당 결과 집합으로 반환될 행 개수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-105">When cursors generate a keyset for a result set, the query optimizer estimates the number of rows that will be returned for that result set.</span></span> <span data-ttu-id="1443c-106">쿼리 최적화 프로그램의 계산 결과, 반환된 행 개수가 이 임계값보다 크면 커서가 계속 채워지는 동안 사용자가 커서에서 행을 인출할 수 있도록 커서가 비동기적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-106">If the query optimizer estimates that the number of returned rows is greater than this threshold, the cursor is generated asynchronously, allowing the user to fetch rows from the cursor while the cursor continues to be populated.</span></span> <span data-ttu-id="1443c-107">그렇지 않으면 커서가 동기적으로 생성되어 모든 행이 반환될 때까지 쿼리가 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-107">Otherwise, the cursor is generated synchronously, and the query waits until all rows are returned.</span></span>  
  
 <span data-ttu-id="1443c-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1443c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1443c-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1443c-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1443c-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1443c-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1443c-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1443c-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1443c-112">보안</span><span class="sxs-lookup"><span data-stu-id="1443c-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1443c-113">**커서 임계값 옵션을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="1443c-113">**To configure the cursor threshold option, using:**</span></span>  
  
     [<span data-ttu-id="1443c-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1443c-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1443c-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1443c-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="1443c-116">**후속 작업:**  [커서 임계값 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1443c-116">**Follow Up:**  [After you configure the cursor threshold option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1443c-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1443c-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1443c-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1443c-118">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1443c-119">에서는 키 집합 커서 또는 정적 [!INCLUDE[tsql](../../includes/tsql-md.md)] 커서를 비동기식으로 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-119">does not support generating keyset-driven or static [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors asynchronously.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1443c-120">커서 작업은 일괄 처리되므로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 커서를 비동기식으로 생성하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-120">cursor operations such as OPEN or FETCH are batched, so there is no need for the asynchronous generation of [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1443c-121">에서는 각 커서 작업의 클라이언트 왕복 때문에 짧은 대기 시간 OPEN이 문제가 되는 비동기 키 집합 기반 또는 정적 API(애플리케이션 프로그래밍 인터페이스) 서버 커서를 계속 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-121">continues to support asynchronous keyset-driven or static application programming interface (API) server cursors where low latency OPEN is a concern, due to client round trips for each cursor operation.</span></span>  
  
-   <span data-ttu-id="1443c-122">키 집합의 예상 행 개수를 결정하는 최적화 프로그램의 정확도는 커서에 있는 각 테이블 통계의 통용성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-122">The accuracy of the query optimizer to determine an estimate for the number of rows in a keyset depends on the currency of the statistics for each of the tables in the cursor.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1443c-123">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1443c-123">Recommendations</span></span>  
  
-   <span data-ttu-id="1443c-124">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="1443c-125">**커서 임계값** 을 -1로 설정하면 모든 키 집합이 동기적으로 생성되므로 작은 커서 집합에 유리합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-125">If you set **cursor threshold** to -1, all keysets are generated synchronously, which benefits small cursor sets.</span></span> <span data-ttu-id="1443c-126">**cursor threshold** 를 0으로 설정하면 모든 커서 키 집합이 비동기적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-126">If you set **cursor threshold** to 0, all cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="1443c-127">다른 값을 사용하면 쿼리 최적화 프로그램이 커서 집합에 있는 예상 행 개수를 비교하여 이 값이 **cursor threshold**에 설정된 수를 초과하면 비동기적으로 키 집합을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-127">With other values, the query optimizer compares the number of expected rows in the cursor set and builds the keyset asynchronously if it exceeds the number set in **cursor threshold**.</span></span> <span data-ttu-id="1443c-128">결과 집합이 작을수록 동기적 작성 성능이 향상되므로 **커서 임계값** 를 너무 낮게 설정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-128">Do not set **cursor threshold** too low, because small result sets are better built synchronously.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1443c-129">보안</span><span class="sxs-lookup"><span data-stu-id="1443c-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1443c-130">권한</span><span class="sxs-lookup"><span data-stu-id="1443c-130">Permissions</span></span>  
 <span data-ttu-id="1443c-131">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="1443c-132">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="1443c-133">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1443c-134">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1443c-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="1443c-135">커서 임계값 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1443c-135">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="1443c-136">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1443c-137">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-137">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="1443c-138">**기타**에서 **커서 임계값** 옵션을 원하는 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-138">Under **Miscellaneous**, change the **Cursor Threshold** option to the value you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1443c-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1443c-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="1443c-140">커서 임계값 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1443c-140">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="1443c-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1443c-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1443c-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1443c-144">다음 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 통해 `cursor threshold` 옵션을 `0` 으로 설정하여 커서 키 집합이 비동기적으로 생성되도록 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the `cursor threshold` option to `0` so that cursor keysets are generated asynchronously.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="1443c-145">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-145">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cursor-threshold-option"></a><a name="FollowUp"></a> <span data-ttu-id="1443c-146">후속 작업: 커서 임계값 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="1443c-146">Follow Up: After you configure the cursor threshold option</span></span>  
 <span data-ttu-id="1443c-147">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1443c-147">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1443c-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1443c-148">See Also</span></span>  
 <span data-ttu-id="1443c-149">[@@CURSOR_ROWS&#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1443c-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span></span>  
 <span data-ttu-id="1443c-150">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1443c-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="1443c-151">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1443c-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="1443c-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1443c-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="1443c-153">UPDATE STATISTICS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1443c-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
