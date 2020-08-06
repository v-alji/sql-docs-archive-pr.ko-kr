---
title: '옵션 (쿼리 실행: SQL Server: 고급 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: rothja
ms.author: jroth
ms.openlocfilehash: 3efc3dc8b42fc08969cc1afb85d4e629f6759e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660112"
---
# <a name="options-query-executionsql-serveradvanced-page"></a><span data-ttu-id="37a1d-102">옵션(쿼리 실행:SQL Server:고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="37a1d-102">Options (Query Execution:SQL Server:Advanced Page)</span></span>
  <span data-ttu-id="37a1d-103">SET 명령을 사용할 때 이용할 수 있는 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-103">Several options are available using the SET command.</span></span> <span data-ttu-id="37a1d-104">이 페이지를 사용하면 SQL Server 쿼리 편집기에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리 실행에 대한 **set** 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-104">Use this page to specify a **set** option for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries in the SQL Server Query Editor.</span></span> <span data-ttu-id="37a1d-105">설정한 옵션은 다른 코드 편집기에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-105">They have no effect on other code editors.</span></span> <span data-ttu-id="37a1d-106">이러한 옵션의 변경 사항은 새로운 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-106">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="37a1d-107">현재 쿼리에 대한 옵션을 변경하려면 **쿼리** 메뉴 또는 **쿼리 창의 바로 가기 메뉴에서** 쿼리 옵션 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 을 클릭하고</span><span class="sxs-lookup"><span data-stu-id="37a1d-107">To change the options for the current queries, click **Query Options** on the **Query** menu or the shortcut menu of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window.</span></span> <span data-ttu-id="37a1d-108">**실행**에서 **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-108">Under **Execution**, click **Advanced**.</span></span> <span data-ttu-id="37a1d-109">각 옵션에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="37a1d-109">For more information on each of these, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="37a1d-110">옵션</span><span class="sxs-lookup"><span data-stu-id="37a1d-110">Options</span></span>  
 <span data-ttu-id="37a1d-111">**SET NOCOUNT**</span><span class="sxs-lookup"><span data-stu-id="37a1d-111">**SET NOCOUNT**</span></span>  
 <span data-ttu-id="37a1d-112">행 개수를 결과 집합이 포함된 메시지로 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-112">Does not return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="37a1d-113">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-113">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-114">**SET NOEXEC**</span><span class="sxs-lookup"><span data-stu-id="37a1d-114">**SET NOEXEC**</span></span>  
 <span data-ttu-id="37a1d-115">쿼리를 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-115">Does not run the query.</span></span> <span data-ttu-id="37a1d-116">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-116">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-117">**SET PARSEONLY**</span><span class="sxs-lookup"><span data-stu-id="37a1d-117">**SET PARSEONLY**</span></span>  
 <span data-ttu-id="37a1d-118">각 쿼리 구문을 검사하지만 쿼리를 실행하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-118">Checks the syntax of each query but does not run the queries.</span></span> <span data-ttu-id="37a1d-119">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-119">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-120">**SET CONCAT_NULL_YIELDS_NULL**</span><span class="sxs-lookup"><span data-stu-id="37a1d-120">**SET CONCAT_NULL_YIELDS_NULL**</span></span>  
 <span data-ttu-id="37a1d-121">이 확인란을 선택하면 기존 값에 NULL을 연결하는 쿼리의 경우 결과로 항상 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-121">When this check box is selected, queries that concatenate an existing value with a NULL, always return a NULL as the result.</span></span> <span data-ttu-id="37a1d-122">이 확인란의 선택을 취소하면 NULL과 연결된 기존 값이 기존 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-122">When this check box is cleared, an existing value concatenated with a NULL, returns the existing value.</span></span> <span data-ttu-id="37a1d-123">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-123">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="37a1d-124">**SET ARITHABORT**</span><span class="sxs-lookup"><span data-stu-id="37a1d-124">**SET ARITHABORT**</span></span>  
 <span data-ttu-id="37a1d-125">이 확인란을 선택하면 식 평가 중 INSERT, DELETE 또는 UPDATE 문에서 산술 오류(오버플로, 0으로 나누기, 도메인 오류)가 발생할 경우 쿼리나 일괄 처리가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-125">When this check box is selected, when an INSERT, DELETE, or UPDATE statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="37a1d-126">이 확인란의 선택을 취소하면 가능한 경우 해당 값에 대해 NULL이 제공되고 쿼리가 계속 실행되며 결과에 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-126">When this check box is cleared, a NULL is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="37a1d-127">자세한 내용은 [SET ARITHABORT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37a1d-127">For more information, see [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span></span> <span data-ttu-id="37a1d-128">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-128">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="37a1d-129">**SET SHOWPLAN_TEXT**</span><span class="sxs-lookup"><span data-stu-id="37a1d-129">**SET SHOWPLAN_TEXT**</span></span>  
 <span data-ttu-id="37a1d-130">이 확인란을 선택하면 각 쿼리에 대한 쿼리 계획이 텍스트 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-130">When this check box is selected, the query plan is returned in text format with each query.</span></span> <span data-ttu-id="37a1d-131">이 확인란은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-131">This check box cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-132">**SET STATISTICS TIME**</span><span class="sxs-lookup"><span data-stu-id="37a1d-132">**SET STATISTICS TIME**</span></span>  
 <span data-ttu-id="37a1d-133">이 확인란을 선택하면 각 쿼리의 시간 통계가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-133">When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="37a1d-134">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-134">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-135">**SET STATISTICS IO**</span><span class="sxs-lookup"><span data-stu-id="37a1d-135">**SET STATISTICS IO**</span></span>  
 <span data-ttu-id="37a1d-136">이 확인란을 선택하면 각 쿼리의 입출력 통계가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-136">When this check box is selected, statistics regarding input and output are returned with each query.</span></span> <span data-ttu-id="37a1d-137">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-137">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-138">**SET TRANSACTION ISOLATION LEVEL**</span><span class="sxs-lookup"><span data-stu-id="37a1d-138">**SET TRANSACTION ISOLATION LEVEL**</span></span>  
 <span data-ttu-id="37a1d-139">기본적으로 READ COMMITTED 트랜잭션 격리 수준이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-139">The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="37a1d-140">자세한 내용은 [SET TRANSACTION ISOLATION LEVEL&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37a1d-140">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="37a1d-141">SNAPSHOT 트랜잭션 격리 수준은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-141">SNAPSHOT transaction isolation level is not available.</span></span> <span data-ttu-id="37a1d-142">SNAPSHOT 격리를 사용하려면 다음 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-142">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 <span data-ttu-id="37a1d-143">**SET DEADLOCK PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="37a1d-143">**SET DEADLOCK PRIORITY**</span></span>  
 <span data-ttu-id="37a1d-144">기본값인 Normal은 교착 상태가 발생할 경우 각 쿼리가 동일한 우선 순위를 가지도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-144">The default value of Normal allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="37a1d-145">해당 쿼리를 교착 상태를 해제하고 종료할 쿼리로 선택하려면 Low 우선 순위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-145">Select a priority of Low if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>  
  
 <span data-ttu-id="37a1d-146">**SET LOCK TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="37a1d-146">**SET LOCK TIMEOUT**</span></span>  
 <span data-ttu-id="37a1d-147">기본값 -1은 트랜잭션이 완료될 때까지 잠금이 유지된다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-147">The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="37a1d-148">0은 기다리지 않음을 나타내고 잠금이 있으면 바로 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-148">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="37a1d-149">트랜잭션 잠금을 이 시간보다 오래 유지해야 하는 경우 0밀리초보다 큰 값을 지정하여 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-149">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>  
  
 <span data-ttu-id="37a1d-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="37a1d-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span></span>  
 <span data-ttu-id="37a1d-151">**QUERY_GOVERNOR_COST_LIMIT** 옵션을 사용하여 쿼리를 실행할 수 있는 시간의 상한값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-151">Use the **QUERY_GOVERNOR_COST_LIMIT** option to specify an upper limit for the time in which a query can run.</span></span> <span data-ttu-id="37a1d-152">쿼리 비용이란 특정 하드웨어 구성에서 쿼리를 완료하는 데 필요한 예상 소요 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-152">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="37a1d-153">기본 설정인 0은 쿼리 실행 시간에 제한이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-153">The default setting of 0 indicates no limit to the length of time a query will run.</span></span>  
  
 <span data-ttu-id="37a1d-154">**공급자 메시지 머리글 무시**</span><span class="sxs-lookup"><span data-stu-id="37a1d-154">**Suppress provider message headers**</span></span>  
 <span data-ttu-id="37a1d-155">이 확인란을 선택하면 SQLClient 공급자와 같은 공급자의 상태 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-155">When this check box is selected, status messages from the provider (such as the SQLClient provider) are not displayed.</span></span> <span data-ttu-id="37a1d-156">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-156">This check box is selected by default.</span></span> <span data-ttu-id="37a1d-157">공급자 수준에서 오류가 발생할 수 있는 쿼리 문제를 해결할 때 공급자 메시지를 보려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-157">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>  
  
 <span data-ttu-id="37a1d-158">**쿼리 실행 후 연결 끊기**</span><span class="sxs-lookup"><span data-stu-id="37a1d-158">**Disconnect after the query executes**</span></span>  
 <span data-ttu-id="37a1d-159">이 확인란을 선택하면 쿼리 실행이 완료된 후 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-159">When this check box is selected, the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is terminated after the query completes.</span></span> <span data-ttu-id="37a1d-160">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-160">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="37a1d-161">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="37a1d-161">**Reset to Default**</span></span>  
 <span data-ttu-id="37a1d-162">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="37a1d-162">Resets all values on this page to the original default values.</span></span>  
  
  
