---
title: 트랜잭션 내구성 제어 | Microsoft 문서
ms.custom: ''
ms.date: 05/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- delayed durability
- Lazy Commit
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f37bcaf8719f4a2f3b1e7fbca1cf332717bd936e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649542"
---
# <a name="control-transaction-durability"></a><span data-ttu-id="5da10-102">트랜잭션 내구성 제어</span><span class="sxs-lookup"><span data-stu-id="5da10-102">Control Transaction Durability</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5da10-103">트랜잭션 커밋은 완전 내구성( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본값)이 있거나 지연된 내구성(느린 커밋이라고도 함)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-103">transaction commits can be either fully durable, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default, or delayed durable (also known as lazy commit).</span></span>  
  
 <span data-ttu-id="5da10-104">완전 내구성이 있는 트랜잭션 커밋은 동기적이므로 트랜잭션에 대한 로그 레코드가 디스크에 기록된 후에만 커밋을 성공으로 보고하고 클라이언트에 컨트롤을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-104">Fully durable transaction commits are synchronous and report a commit as successful and return control to the client only after the log records for the transaction are written to disk.</span></span> <span data-ttu-id="5da10-105">지연된 내구성이 있는 트랜잭션 커밋은 비동기적이므로 트랜잭션에 대한 로그 레코드가 디스크에 기록되기 전에 커밋을 성공으로 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-105">Delayed durable transaction commits are asynchronous and report a commit as successful before the log records for the transaction are written to disk.</span></span> <span data-ttu-id="5da10-106">트랜잭션이 내구성을 가지려면 디스크에 트랜잭션 로그 항목을 기록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-106">Writing the transaction log entries to disk is required for a transaction to be durable.</span></span> <span data-ttu-id="5da10-107">지연된 내구성이 있는 트랜잭션은 트랜잭션 로그 항목을 디스크에 플러시한 경우에 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-107">Delayed durable transactions become durable when the transaction log entries are flushed to disk.</span></span>  
  
 <span data-ttu-id="5da10-108">이 항목에서는 지연된 내구성이 있는 트랜잭션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-108">This topic details delayed durable transactions.</span></span>  
  
## <a name="full-vs-delayed-transaction-durability"></a><span data-ttu-id="5da10-109">완전 트랜잭션 내구성과 지연된 트랜잭션 내구성 비교</span><span class="sxs-lookup"><span data-stu-id="5da10-109">Full vs. Delayed Transaction Durability</span></span>  
 <span data-ttu-id="5da10-110">완전 트랜잭션 내구성과 지연된 트랜잭션 내구성은 모두 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-110">Both full and delayed transaction durability have their advantages and disadvantages.</span></span> <span data-ttu-id="5da10-111">애플리케이션은 완전 내구성이 있는 트랜잭션과 지연된 내구성이 있는 트랜잭션을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-111">An application can have a mix of fully and delayed durable transactions.</span></span> <span data-ttu-id="5da10-112">따라서 비즈니스 요구 사항과 각 트랜잭션이 이러한 요구 사항에 얼마나 적합한지를 신중하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-112">You should carefully consider your business needs and how each fits into those needs.</span></span>  
  
### <a name="full-transaction-durability"></a><span data-ttu-id="5da10-113">완전 트랜잭션 내구성</span><span class="sxs-lookup"><span data-stu-id="5da10-113">Full transaction durability</span></span>  
 <span data-ttu-id="5da10-114">완전 내구성이 있는 트랜잭션은 클라이언트에 컨트롤을 반환하기 전에 디스크에 트랜잭션 로그를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-114">Fully durable transactions write the transaction log to disk before returning control to the client.</span></span> <span data-ttu-id="5da10-115">다음과 같은 경우 완전 내구성이 있는 트랜잭션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-115">You should use fully durable transactions whenever:</span></span>  
  
-   <span data-ttu-id="5da10-116">시스템에서 데이터 손실을 허용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-116">Your system cannot tolerate any data loss.</span></span>   
    <span data-ttu-id="5da10-117">데이터 일부를 손실할 수 있는 경우에 대한 자세한 내용은 [데이터를 손실할 수는 경우](#when-can-i-lose-data) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-117">See the section [When can I lose data?](#when-can-i-lose-data) for information on when you can lose some of your data.</span></span>  
  
-   <span data-ttu-id="5da10-118">병목 현상의 원인이 트랜잭션 로그 쓰기 대기 시간이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-118">The bottleneck is not due to transaction log write latency.</span></span>  
  
 <span data-ttu-id="5da10-119">지연된 트랜잭션 내구성은 트랜잭션 로그 레코드를 메모리에 유지하고 트랜잭션 로그에 일괄적으로 쓰기 때문에 I/O 작업이 더 적게 수행되므로 I/O 기록으로 인한 대기 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-119">Delayed transaction durability reduces the latency due to log I/O by keeping the transaction log records in memory and writing to the transaction log in batches, thus requiring fewer I/O operations.</span></span> <span data-ttu-id="5da10-120">지연된 트랜잭션 내구성은 로그 I/O 경합을 줄여서 시스템의 대기 시간을 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-120">Delayed transaction durability potentially reduces log I/O contention, thus reducing waits in the system.</span></span>  
  
 <span data-ttu-id="5da10-121">**완전 트랜잭션 내구성 보장**</span><span class="sxs-lookup"><span data-stu-id="5da10-121">**Full Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="5da10-122">트랜잭션 커밋에 성공하면 트랜잭션에 의한 변경 사항이 시스템의 다른 트랜잭션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-122">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span> <span data-ttu-id="5da10-123">자세한 내용은 [트랜잭션 격리 수준](../../database-engine/transaction-isolation-levels.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-123">See the topic [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for more information.</span></span>  
  
-   <span data-ttu-id="5da10-124">내구성이 커밋에서 보장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-124">Durability is guaranteed on commit.</span></span> <span data-ttu-id="5da10-125">트랜잭션 커밋이 성공하여 클라이언트에 컨트롤을 반환하기 이전에는 해당 로그 레코드가 디스크에 지속됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-125">Corresponding log records are persisted to disk before the transaction commit succeeds and returns control to the client.</span></span>  
  
### <a name="delayed-transaction-durability"></a><span data-ttu-id="5da10-126">지연된 트랜잭션 내구성</span><span class="sxs-lookup"><span data-stu-id="5da10-126">Delayed transaction durability</span></span>  
 <span data-ttu-id="5da10-127">지연된 트랜잭션 내구성은 디스크에 대한 비동기 로그 쓰기를 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-127">Delayed transaction durability is accomplished using asynchronous log writes to disk.</span></span> <span data-ttu-id="5da10-128">트랜잭션 로그 레코드는 버퍼에 유지되며 버퍼가 꽉 차거나 버퍼 플러시 이벤트가 발생하면 디스크에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-128">Transaction log records are kept in a buffer and written to disk when the buffer fills or a buffer flushing event takes place.</span></span> <span data-ttu-id="5da10-129">지연된 트랜잭션 내구성은 다음과 같은 이유로 시스템에서 대기 시간과 경합을 모두 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-129">Delayed transaction durability reduces both latency and contention within the system because:</span></span>  
  
-   <span data-ttu-id="5da10-130">로그 IO를 완료하고 클라이언트에 컨트롤을 반환할 때까지 트랜잭션 커밋 처리가 지연되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-130">The transaction commit processing does not wait for log IO to finish and return control to the client.</span></span>  
  
-   <span data-ttu-id="5da10-131">동시 트랜잭션이 로그 IO를 경합할 가능성이 낮습니다. 대신 더 큰 청크로 구성된 디스크에 로그 버퍼를 플러시하여 경합을 줄이고 처리 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-131">Concurrent transactions are less likely to contend for log IO; instead, the log buffer can be flushed to disk in larger chunks, reducing contention, and increasing throughput.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5da10-132">동시성이 높은 경우 특히, 로그 버퍼를 플러시 속도보다 더 빠르게 채울 경우 로그 I/O 경합이 여전히 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-132">You may still have log I/O contention if there is a high degree of concurrency, particularly if you fill up the log buffer faster than you flush it.</span></span>  
  
 <span data-ttu-id="5da10-133">**지연된 트랜잭션 내구성을 사용할 경우**</span><span class="sxs-lookup"><span data-stu-id="5da10-133">**When to use delayed transaction durability**</span></span>  
  
 <span data-ttu-id="5da10-134">지연된 트랜잭션 내구성을 사용하는 것이 유리한 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-134">Some of the cases in which you could benefit from using delayed transaction durability are:</span></span>  
  
 <span data-ttu-id="5da10-135">**약간의 데이터 손실을 허용할 수 있는 경우**</span><span class="sxs-lookup"><span data-stu-id="5da10-135">**You can tolerate some data loss.**</span></span>  
 <span data-ttu-id="5da10-136">약간의 데이터 손실을 허용할 수 있는 경우(예: 대부분의 데이터를 보유하여 개별 데이터가 중요하지는 않은 경우)에는 지연된 내구성을 고려하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-136">If you can tolerate some data loss, for example, where individual records are not critical as long as you have most of the data, then delayed durability may be worth considering.</span></span> <span data-ttu-id="5da10-137">데이터 손실을 허용할 수 없는 경우에는 지연된 트랜잭션 내구성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-137">If you cannot tolerate any data loss, do not use delayed transaction durability.</span></span>  
  
 <span data-ttu-id="5da10-138">**트랜잭션 로그 쓰기 중에 병목 현상이 발생하는 경우**</span><span class="sxs-lookup"><span data-stu-id="5da10-138">**You are experiencing a bottleneck on transaction log writes.**</span></span>  
 <span data-ttu-id="5da10-139">트랜잭션 로그 쓰기의 지연으로 인해 성능 문제가 발생하는 경우 애플리케이션에서 지연된 트랜잭션 내구성을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-139">If your performance issues are due to latency in transaction log writes, your application will likely benefit from using delayed transaction durability.</span></span>  
  
 <span data-ttu-id="5da10-140">**작업의 경합률이 높은 경우**</span><span class="sxs-lookup"><span data-stu-id="5da10-140">**Your workloads have a high contention rate.**</span></span>  
 <span data-ttu-id="5da10-141">작업의 경합 수준이 높은 경우 잠금이 해제되는 동안 대기하는 데 많은 시간이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-141">If your system has workloads with a high contention level much time is lost waiting for locks to be released.</span></span> <span data-ttu-id="5da10-142">지연된 트랜잭션 내구성은 커밋 시간을 단축하여 잠금을 더 빠르게 해제하여 처리 속도를 높입니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-142">Delayed transaction durability reduces commit time and thus releases locks faster which results in higher throughput.</span></span>  
  
 <span data-ttu-id="5da10-143">**지연된 트랜잭션 내구성 보장**</span><span class="sxs-lookup"><span data-stu-id="5da10-143">**Delayed Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="5da10-144">트랜잭션 커밋에 성공하면 트랜잭션에 의한 변경 사항이 시스템의 다른 트랜잭션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-144">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span>  
  
-   <span data-ttu-id="5da10-145">트랜잭션 내구성은 디스크에 메모리 내 트랜잭션 로그를 플러시한 경우에만 보장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-145">Transaction durability is guaranteed only following a flush of the in-memory transaction log to disk.</span></span> <span data-ttu-id="5da10-146">메모리 내 트랜잭션 로그가 디스크에 플러시되는 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-146">The in-memory transaction log is flushed to disk when:</span></span>  
  
    -   <span data-ttu-id="5da10-147">동일한 데이터베이스의 완전 내구성이 있는 트랜잭션이 데이터베이스에서 변경되고 성공적으로 커밋된 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-147">A fully durable transaction in the same database makes a change in the database and successfully commits.</span></span>  
  
    -   <span data-ttu-id="5da10-148">사용자가 시스템 저장 프로시저 `sp_flush_log` 를 성공적으로 실행한 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-148">The user executes the system stored procedure `sp_flush_log` successfully.</span></span>  
  
    -   <span data-ttu-id="5da10-149">메모리 내 트랜잭션 로그 버퍼가 꽉 차서 디스크에 자동으로 플러시되는 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-149">The in-memory transaction log buffer fills up and automatically flushes to disk.</span></span>  
  
     <span data-ttu-id="5da10-150">완전 내구성이 있는 트랜잭션 또는 sp_flush_log가 성공적으로 커밋되면, 이전에 커밋된 지연된 내구성 트랜잭션은 모두 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-150">If a fully durable transaction or sp_flush_log successfully commit, all previously committed delayed durability transactions have been made durable.</span></span>  
  
 <span data-ttu-id="5da10-151">로그는 정기적으로 디스크에 플러시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-151">The log may be flushed to disk periodically.</span></span> <span data-ttu-id="5da10-152">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 내구성 있는 트랜잭션 및 sp_flush_log 외의 어떠한 내구성도 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-152">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not provide any durability guarantees other than durable transactions and sp_flush_log.</span></span>  
  
## <a name="how-to-control-transaction-durability"></a><span data-ttu-id="5da10-153">트랜잭션 내구성을 제어하는 방법</span><span class="sxs-lookup"><span data-stu-id="5da10-153">How to control transaction durability</span></span>  
  
### <a name="database-level-control"></a><span data-ttu-id="5da10-154">데이터베이스 수준 제어</span><span class="sxs-lookup"><span data-stu-id="5da10-154">Database level control</span></span>  
 <span data-ttu-id="5da10-155">DBA는 다음 문을 사용하여 사용자가 데이터베이스에서 지연된 트랜잭션 내구성을 사용할 수 있는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-155">You, the DBA, can control whether users can use delayed transaction durability on a database with the following statement.</span></span> <span data-ttu-id="5da10-156">ALTER DATABASE를 사용하여 지연된 내구성 설정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-156">You must set the delayed durability setting with ALTER DATABASE.</span></span>  
  
```sql  
ALTER DATABASE ... SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
```  
  
 `DISABLED`  
 <span data-ttu-id="5da10-157">[기본값] 이 설정을 사용하면 커밋 수준 설정(DELAYED_DURABILITY=[ON | OFF])에 상관없이 데이터베이스에 커밋된 모든 트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-157">[default] With this setting, all transactions that commit on the database are fully durable, regardless of the commit level setting (DELAYED_DURABILITY=[ON | OFF]).</span></span> <span data-ttu-id="5da10-158">저장 프로시저를 변경하고 다시 컴파일할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-158">There is no need for stored procedure change and recompilation.</span></span> <span data-ttu-id="5da10-159">따라서 지연된 내구성으로 인해 데이터가 위험에 노출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-159">This allows you to ensure that no data is ever put at risk by delayed durability.</span></span>  
  
 `ALLOWED`  
 <span data-ttu-id="5da10-160">이 설정을 사용하면 각 트랜잭션의 내구성이 트랜잭션 수준에서 결정됩니다. 즉, DELAYED_DURABILITY = { *OFF* | ON }에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-160">With this setting, each transaction's durability is determined at the transaction level - DELAYED_DURABILITY = { *OFF* | ON }.</span></span> <span data-ttu-id="5da10-161">자세한 내용은 [Atomic 블록 수준 제어-고유 하 게 컴파일된 저장 프로시저](#atomic-block-level-control---natively-compiled-stored-procedures) 및 [커밋 수준 제어-transact-sql](#commit-level-control---t-sql) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-161">See [Atomic block level control - Natively Compiled Stored Procedures](#atomic-block-level-control---natively-compiled-stored-procedures) and [COMMIT level control - Transact-SQL](#commit-level-control---t-sql) for more information.</span></span>  
  
 `FORCED`  
 <span data-ttu-id="5da10-162">이 설정을 사용하면 데이터베이스에 커밋되는 모든 트랜잭션이 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-162">With this setting, every transaction that commits on the database is delayed durable.</span></span> <span data-ttu-id="5da10-163">트랜잭션이 완전 내구성(DELAYED_DURABILITY = OFF)을 지정하는지 여부에 상관없이 트랜잭션은 지연된 내구성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-163">Whether the transaction specifies fully durable (DELAYED_DURABILITY = OFF) or makes no specification, the transaction is delayed durable.</span></span> <span data-ttu-id="5da10-164">이 설정은 지연된 트랜잭션 내구성이 데이터베이스에 유용하고 애플리케이션 코드를 변경하지 않으려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-164">This setting is useful when delayed transaction durability is useful for a database and you do not want to change any application code.</span></span>  
  
### <a name="atomic-block-level-control---natively-compiled-stored-procedures"></a><span data-ttu-id="5da10-165"> Atomic 블록 수준 제어 – 고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="5da10-165">Atomic block level control - Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="5da10-166">다음 코드는 ATOMIC 블록 내로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-166">The following code goes inside the atomic block.</span></span>  
  
```sql  
DELAYED_DURABILITY = { OFF | ON }  
```  
  
 `OFF`  
 <span data-ttu-id="5da10-167">[기본값] DELAYED_DURABLITY = FORCED 데이터베이스 옵션을 적용하여 커밋이 비동기적이고 지연된 내구성을 갖는 경우를 제외하고 트랜잭션은 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-167">[default] The transaction is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the commit is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="5da10-168">자세한 내용은 [Database level control](#database-level-control) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-168">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="5da10-169">DELAYED_DURABLITY = DISABLED 데이터베이스 옵션을 적용하여 커밋이 동기적이고 완전 내구성이 있는 경우를 제외하고 트랜잭션은 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-169">The transaction is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the commit is synchronous and thus fully durable.</span></span>  <span data-ttu-id="5da10-170">자세한 내용은 [Database level control](#database-level-control) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-170">See [Database level control](#database-level-control) for more information.</span></span>  
  
 <span data-ttu-id="5da10-171">**코드 예:**</span><span class="sxs-lookup"><span data-stu-id="5da10-171">**Example Code:**</span></span>  
  
```sql  
CREATE PROCEDURE <procedureName> ...  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    DELAYED_DURABILITY = ON,  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English'  
    ...  
)  
END  
```  
  
### <a name="table-1-durability-in-atomic-blocks"></a><span data-ttu-id="5da10-172">테이블 1: ATOMIC 블록의 내구성</span><span class="sxs-lookup"><span data-stu-id="5da10-172">Table 1: Durability in Atomic Blocks</span></span>  
  
|<span data-ttu-id="5da10-173">ATOMIC 블록 내구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5da10-173">Atomic block durability option</span></span>|<span data-ttu-id="5da10-174">기존 트랜잭션 없음</span><span class="sxs-lookup"><span data-stu-id="5da10-174">No existing transaction</span></span>|<span data-ttu-id="5da10-175">처리 중인 트랜잭션(완전 또는 지연된 내구성이 있음)</span><span class="sxs-lookup"><span data-stu-id="5da10-175">Transaction in process (fully or delayed durable)</span></span>|  
|------------------------------------|-----------------------------|---------------------------------------------------------|  
|`DELAYED_DURABILITY = OFF`|<span data-ttu-id="5da10-176">ATOMIC 블록은 새로운 완전 내구성이 있는 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-176">Atomic block starts a new fully durable transaction.</span></span>|<span data-ttu-id="5da10-177">ATOMIC 블록은 기존 트랜잭션에 저장점을 만든 다음 새 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-177">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
|`DELAYED_DURABILITY = ON`|<span data-ttu-id="5da10-178">ATOMIC 블록은 새로운 지연된 내구성이 있는 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-178">Atomic block starts a new delayed durable transaction.</span></span>|<span data-ttu-id="5da10-179">ATOMIC 블록은 기존 트랜잭션에 저장점을 만든 다음 새 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-179">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
  
### <a name="commit-level-control---t-sql"></a><span data-ttu-id="5da10-180">커밋 수준 제어-(T-sql)</span><span class="sxs-lookup"><span data-stu-id="5da10-180">COMMIT level control - (T-SQL)</span></span>
 <span data-ttu-id="5da10-181">지연된 트랜잭션 내구성을 강제로 적용할 수 있도록 COMMIT 구문이 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-181">The COMMIT syntax is extended so you can force delayed transaction durability.</span></span> <span data-ttu-id="5da10-182">데이터베이스 수준에서 If DELAYED_DURABILITY가 DISABLED 또는 FORCED인 경우(위 내용 참조) 이 COMMIT 옵션은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-182">If DELAYED_DURABILITY is DISABLED or FORCED at the database level (see above) this COMMIT option is ignored.</span></span>  
  
```sql  
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
  
```  
  
 `OFF`  
 <span data-ttu-id="5da10-183">[기본값] DELAYED_DURABLITY = FORCED 데이터베이스 옵션을 적용하여 COMMIT이 비동기적이고 지연된 내구성을 갖는 경우를 제외하고 COMMIT 트랜잭션은 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-183">[default] The transaction COMMIT is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the COMMIT is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="5da10-184">자세한 내용은 [Database level control](#database-level-control) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-184">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="5da10-185">DELAYED_DURABLITY = DISABLED 데이터베이스 옵션을 적용하여 COMMIT이 동기적이고 완전 내구성이 있는 경우를 제외하고 COMMIT 트랜잭션은 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-185">The transaction COMMIT is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the COMMIT is synchronous and thus fully durable.</span></span> <span data-ttu-id="5da10-186">자세한 내용은 [Database level control](#database-level-control) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-186">See [Database level control](#database-level-control) for more information.</span></span>  
  
### <a name="summary-of-options-and-their-interactions"></a><span data-ttu-id="5da10-187">옵션 및 상호 작용 요약</span><span class="sxs-lookup"><span data-stu-id="5da10-187">Summary of options and their interactions</span></span>  
 <span data-ttu-id="5da10-188">이 표에서는 데이터베이스 수준 지연된 내구성 설정과 커밋 수준 설정 사이의 상호 작용을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-188">This table summarizes the interactions between database level delayed durability settings and commit level settings.</span></span> <span data-ttu-id="5da10-189">데이터베이스 수준 설정이 커밋 수준 설정보다 항상 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-189">Database level settings always take precedence over commit level settings.</span></span>  
  
|<span data-ttu-id="5da10-190">COMMIT 설정/데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="5da10-190">COMMIT setting/Database setting</span></span>|<span data-ttu-id="5da10-191">DELAYED_DURABILITY = DISABLED</span><span class="sxs-lookup"><span data-stu-id="5da10-191">DELAYED_DURABILITY = DISABLED</span></span>|<span data-ttu-id="5da10-192">DELAYED_DURABILITY = ALLOWED</span><span class="sxs-lookup"><span data-stu-id="5da10-192">DELAYED_DURABILITY = ALLOWED</span></span>|<span data-ttu-id="5da10-193">DELAYED_DURABILITY = FORCED</span><span class="sxs-lookup"><span data-stu-id="5da10-193">DELAYED_DURABILITY = FORCED</span></span>|  
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|  
|<span data-ttu-id="5da10-194">`DELAYED_DURABILITY = OFF` 데이터베이스 수준 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="5da10-194">`DELAYED_DURABILITY = OFF` Database level transactions.</span></span>|<span data-ttu-id="5da10-195">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-195">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-196">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-196">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-197">트랜잭션이 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-197">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="5da10-198">`DELAYED_DURABILITY = ON` 데이터베이스 수준 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="5da10-198">`DELAYED_DURABILITY = ON` Database level transactions.</span></span>|<span data-ttu-id="5da10-199">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-199">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-200">트랜잭션이 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-200">Transaction is delayed durable.</span></span>|<span data-ttu-id="5da10-201">트랜잭션이 지연된 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-201">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="5da10-202">`DELAYED_DURABILITY = OFF` 데이터베이스 간 트랜잭션 또는 분산 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="5da10-202">`DELAYED_DURABILITY = OFF` Cross database or distributed transaction.</span></span>|<span data-ttu-id="5da10-203">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-203">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-204">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-204">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-205">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-205">Transaction is fully durable.</span></span>|  
|<span data-ttu-id="5da10-206">`DELAYED_DURABILITY = ON` 데이터베이스 간 트랜잭션 또는 분산 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="5da10-206">`DELAYED_DURABILITY = ON` Cross database or distributed transaction.</span></span>|<span data-ttu-id="5da10-207">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-207">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-208">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-208">Transaction is fully durable.</span></span>|<span data-ttu-id="5da10-209">트랜잭션이 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-209">Transaction is fully durable.</span></span>|  
  
## <a name="how-to-force-a-transaction-log-flush"></a><span data-ttu-id="5da10-210">트랜잭션 로그를 강제로 플러시하는 방법</span><span class="sxs-lookup"><span data-stu-id="5da10-210">How to force a transaction log flush</span></span>  
 <span data-ttu-id="5da10-211">디스크에 트랜잭션 로그를 강제로 플러시하는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-211">There are two means to force flush the transaction log to disk.</span></span>  
  
-   <span data-ttu-id="5da10-212">동일한 데이터베이스를 변경하는 완전 내구성이 있는 트랜잭션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-212">Execute any fully durable transaction that alters the same database.</span></span> <span data-ttu-id="5da10-213">이렇게 하면 모든 이전에 커밋된 지연된 내구성 트랜잭션의 로그 레코드가 디스크에 강제로 플러시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-213">This forces a flush of the log records of all preceding committed delayed durability transactions to disk.</span></span>  
  
-   <span data-ttu-id="5da10-214">시스템 저장 프로시저 실행 `sp_flush_log`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-214">Execute the system stored procedure `sp_flush_log`.</span></span> <span data-ttu-id="5da10-215">이 프로시저는 모든 이전에 커밋된 지연된 내구성이 있는 트랜잭션의 로그 레코드를 디스크에 강제로 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-215">This procedure forces a flush of the log records of all preceding committed delayed durable transactions to disk.</span></span> <span data-ttu-id="5da10-216">자세한 내용은 [sys.sp_flush_log&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-216">For more information see [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql).</span></span>  
  
##  <a name="delayed-durability-and-other-sql-server-features"></a><span data-ttu-id="5da10-217">지연된 내구성 및 기타 SQL Server 설정</span><span class="sxs-lookup"><span data-stu-id="5da10-217">Delayed durability and other SQL Server features</span></span>  
 <span data-ttu-id="5da10-218">**변경 추적 및 변경 데이터 캡처**</span><span class="sxs-lookup"><span data-stu-id="5da10-218">**Change tracking and change data capture**</span></span>  
 <span data-ttu-id="5da10-219">변경 추적을 적용한 모든 트랜잭션은 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-219">All transactions with change tracking are fully durable.</span></span> <span data-ttu-id="5da10-220">변경 추적을 사용하도록 설정한 테이블에 쓰기 작업을 수행하는 경우 트랜잭션은 변경 추적 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-220">A transaction has the change tracking property if it does any write operations to tables that are enabled for change tracking.</span></span> <span data-ttu-id="5da10-221">지연된 내구성 사용은 CDC(변경 데이터 캡처)를 사용하는 데이터베이스에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-221">The use of delayed durability is not supported for databases which use change data capture (CDC).</span></span>   
  
 <span data-ttu-id="5da10-222">**충돌 복구**</span><span class="sxs-lookup"><span data-stu-id="5da10-222">**Crash recovery**</span></span>  
 <span data-ttu-id="5da10-223">일관성이 보장되지만 커밋된 지연된 내구성이 있는 트랜잭션에서 변경된 일부 항목이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-223">Consistency is guaranteed, but some changes from delayed durable transactions that have committed may be lost.</span></span>  
  
 <span data-ttu-id="5da10-224">**데이터베이스 간 및 DTC**</span><span class="sxs-lookup"><span data-stu-id="5da10-224">**Cross-database and DTC**</span></span>  
 <span data-ttu-id="5da10-225">데이터베이스 또는 트랜잭션 커밋 설정에 상관없이 데이터베이스 간 트랜잭션 또는 분산 트랜잭션인 경우 트랜잭션은 완전 내구성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-225">If a transaction is cross-database or distributed, if is fully durable, regardless of any database or transaction commit setting.</span></span>  
  
 <span data-ttu-id="5da10-226">**AlwaysOn 가용성 그룹 및 미러링**</span><span class="sxs-lookup"><span data-stu-id="5da10-226">**Always On Availability Groups and Mirroring**</span></span>  
 <span data-ttu-id="5da10-227">지연된 내구성이 있는 트랜잭션은 기본 또는 보조 데이터베이스에서 내구성을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-227">Delayed durable transactions do not guarantee any durability on either the primary or any of the secondaries.</span></span> <span data-ttu-id="5da10-228">또한 보조 데이터베이스에서 트랜잭션에 대한 정보를 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-228">In addition, they do not guarantee any knowledge about the transaction at the secondary.</span></span> <span data-ttu-id="5da10-229">제어는 커밋 후 동기 보조 데이터베이스에서 승인이 수신되기 이전에 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-229">After commit, control is returned to the client before any acknowledgement is received from any synchronous secondary.</span></span>  
  
 <span data-ttu-id="5da10-230">**장애 조치(Failover) 클러스터링**</span><span class="sxs-lookup"><span data-stu-id="5da10-230">**Failover clustering**</span></span>  
 <span data-ttu-id="5da10-231">일부 지연된 내구성이 있는 트랜잭션 쓰기가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-231">Some delayed durable transaction writes might be lost.</span></span>  
  
 <span data-ttu-id="5da10-232">**트랜잭션 복제**</span><span class="sxs-lookup"><span data-stu-id="5da10-232">**Transaction Replication**</span></span>  
 <span data-ttu-id="5da10-233">지연된 내구성이 있는 트랜잭션은 트랜잭션 복제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-233">Delayed durable transactions is not supported with Transactional Replication.</span></span>  
  
 <span data-ttu-id="5da10-234">**로그 전달**</span><span class="sxs-lookup"><span data-stu-id="5da10-234">**Log shipping**</span></span>  
 <span data-ttu-id="5da10-235">내구성이 있는 트랜잭션만 발송되는 로그에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-235">Only transactions that have been made durable are included in the log that is shipped.</span></span>  
  
 <span data-ttu-id="5da10-236">**로그 백업**</span><span class="sxs-lookup"><span data-stu-id="5da10-236">**Log Backup**</span></span>  
 <span data-ttu-id="5da10-237">내구성이 있는 트랜잭션만 백업에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-237">Only transactions that have been made durable are included in the backup.</span></span>  
  
## <a name="when-can-i-lose-data"></a><span data-ttu-id="5da10-238">데이터를 손실할 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="5da10-238">When can I lose data?</span></span>  
 <span data-ttu-id="5da10-239">테이블에 대해 지연된 내구성을 구현하는 경우 특정 상황에서 데이터를 손실할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-239">If you implement delayed durability on any of your tables, you should understand that certain circumstances can lead to data loss.</span></span> <span data-ttu-id="5da10-240">데이터 손실을 허용할 수 없는 경우에는 지연된 트랜잭션 내구성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-240">If you cannot tolerate any data loss, you should not use delayed durability on your tables.</span></span>  
  
### <a name="catastrophic-events"></a><span data-ttu-id="5da10-241">재해</span><span class="sxs-lookup"><span data-stu-id="5da10-241">Catastrophic events</span></span>  
 <span data-ttu-id="5da10-242">서버 크래시와 같은 재해 발생 시 디스크에 저장되지 않은 커밋된 모든 트랜잭션의 데이터를 손실하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-242">In the case of a catastrophic event, like a server crash, you will lose the data for all committed transactions that have not been saved to disk.</span></span> <span data-ttu-id="5da10-243">데이터베이스의 모든 테이블(내구성 있는 메모리 최적화 테이블 또는 디스크 기반 테이블)에 대해 완전 내구성이 있는 트랜잭션이 실행되거나 `sp_flush_log`가 호출될 때마다 지연된 내구성 트랜잭션이 디스크에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-243">Delayed durable transactions are saved to disk whenever a fully durable transaction is executed against any table (durable memory-optimized or disk-based) in the database, or `sp_flush_log` is called.</span></span> <span data-ttu-id="5da10-244">지연된 내구성 트랜잭션을 사용하는 경우 데이터베이스에 정기적으로 `sp_flush_log` 를 업데이트하거나 호출할 수 있는 작은 테이블을 만들어 처리되지 않은 커밋된 모든 트랜잭션을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-244">If you are using delayed durable transactions, you may want to create a small table in the database that you can periodically update or periodically call `sp_flush_log` to save all outstanding committed transactions.</span></span> <span data-ttu-id="5da10-245">또한 가득 찰 때마다 트랜잭션 로그가 플러시되지만 이는 예측하기 어려워 제어하는 것이 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-245">The transaction log also flushes whenever it becomes full, but that is hard to predict and impossible to control.</span></span>  
  
### <a name="sql-server-shutdown-and-restart"></a><span data-ttu-id="5da10-246">SQL Server 종료 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="5da10-246">SQL Server shutdown and restart</span></span>  
 <span data-ttu-id="5da10-247">지연된 내구성의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 예기치 않은 종료와 예상된 종료/다시 시작 간에는 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-247">For delayed durability, there is no difference between an unexpected shutdown and an expected shutdown/restart of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5da10-248">재해와 같은 데이터 손실을 대비하여 계획을 세워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-248">Like catastrophic events, you should plan for data loss.</span></span> <span data-ttu-id="5da10-249">예정된 종료/다시 시작에서 디스크에 기록되지 않은 일부 트랜잭션이 먼저 디스크에 저장될 수 있지만 이에 대한 계획을 세우지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da10-249">In a planned shutdown/restart some transactions that have not been written to disk may first be saved to disk, but you should not plan on it.</span></span> <span data-ttu-id="5da10-250">예정되었든 예정되지 않았든 종료/다시 시작 시 재해와 동일하게 데이터를 손실할 것처럼 계획을 세우세요.</span><span class="sxs-lookup"><span data-stu-id="5da10-250">Plan as though a shutdown/restart, whether planned or unplanned, loses the data the same as a catastrophic event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da10-251">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5da10-251">See Also</span></span>  
 <span data-ttu-id="5da10-252">[트랜잭션 격리 수준](../../database-engine/transaction-isolation-levels.md) </span><span class="sxs-lookup"><span data-stu-id="5da10-252">[Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) </span></span>  
 [<span data-ttu-id="5da10-253">메모리 액세스에 최적화된 테이블의 트랜잭션 격리 수준에 대한 지침</span><span class="sxs-lookup"><span data-stu-id="5da10-253">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)  
  
  
