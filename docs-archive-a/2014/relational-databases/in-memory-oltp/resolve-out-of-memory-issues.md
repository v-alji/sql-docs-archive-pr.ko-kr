---
title: OOM(메모리 부족) 문제 해결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5f57725d559b0cd62679550e2bb7c04dbd7e2bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649552"
---
# <a name="resolve-out-of-memory-issues"></a><span data-ttu-id="2a87c-102">OOM(메모리 부족) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-102">Resolve Out Of Memory Issues</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="2a87c-103">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 다른 방법으로 더 많은 메모리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-103">uses more memory and in different ways than does [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2a87c-104">필요 증가에 따라 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 에 대해 설치하고 할당한 메모리의 양이 불충분해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-104">It is possible that the amount of memory you installed and allocated for [!INCLUDE[hek_2](../../includes/hek-2-md.md)] becomes inadequate for your growing needs.</span></span> <span data-ttu-id="2a87c-105">이 경우 메모리가 부족해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-105">If so, you could run out of memory.</span></span> <span data-ttu-id="2a87c-106">이 항목에서는 OOM 상황에서 복구하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-106">This topic covers how to recover from an OOM situation.</span></span> <span data-ttu-id="2a87c-107">여러 OOM 상황을 방지하는 데 도움이 될 수 있는 지침은 [메모리 사용량 모니터링 및 문제 해결](monitor-and-troubleshoot-memory-usage.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-107">See [Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) for guidance that can help you avoid many OOM situations.</span></span>  
  
## <a name="covered-in-this-topic"></a><span data-ttu-id="2a87c-108">이 항목의 내용</span><span class="sxs-lookup"><span data-stu-id="2a87c-108">Covered in this topic</span></span>  
  
|<span data-ttu-id="2a87c-109">항목</span><span class="sxs-lookup"><span data-stu-id="2a87c-109">Topic</span></span>|<span data-ttu-id="2a87c-110">개요</span><span class="sxs-lookup"><span data-stu-id="2a87c-110">Overview</span></span>|  
|-----------|--------------|  
| [<span data-ttu-id="2a87c-111">OOM으로 인한 데이터베이스 복원 실패 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-111">Resolve database restore failures due to OOM</span></span>](#resolve-database-restore-failures-due-to-oom) |<span data-ttu-id="2a87c-112">"' *\<resourcePoolName>* ' 리소스 풀의 메모리 부족으로 인해 ' *\<databaseName>* ' 데이터베이스에 대한 복원 작업이 실패했습니다"라는 오류 메시지가 나타나는 경우 수행할 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-112">What to do if you get the error message, "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'."</span></span>|  
| [<span data-ttu-id="2a87c-113">메모리 부족 또는 OOM 상황이 작업에 미치는 영향 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-113">Resolve impact of low memory or OOM conditions on the workload</span></span>](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|<span data-ttu-id="2a87c-114">메모리 부족 문제가 성능에 부정적인 영향을 미치고 있음을 발견할 경우 수행할 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-114">What to do if you find low memory issues are negatively impacting performance.</span></span>|  
| [<span data-ttu-id="2a87c-115">사용 가능한 메모리가 충분한 경우 메모리 부족으로 인한 페이지 할당 오류 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-115">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |<span data-ttu-id="2a87c-116">작업에 사용할 수 있는 메모리가 충분한데 "' *\<resourcePoolName>* ' 리소스 풀의 메모리 부족으로 인해 ' *\<databaseName>* ' 데이터베이스에 대해 페이지를 할당할 수 없습니다"라는</span><span class="sxs-lookup"><span data-stu-id="2a87c-116">What to do if you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="2a87c-117">오류 메시지가 나타나는 경우 수행할 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-117">..." when available memory is sufficient for the operation.</span></span>|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a><span data-ttu-id="2a87c-118">OOM으로 인한 데이터베이스 복원 실패 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-118">Resolve database restore failures due to OOM</span></span>  
 <span data-ttu-id="2a87c-119">데이터베이스를 복원 하려고 하면 "' *\<databaseName>* ' 리소스 풀의 메모리 부족으로 인해 ' ' 데이터베이스에 대 한 복원 작업이 실패 했습니다." 라는 오류 메시지가 표시 될 수 있습니다 *\<resourcePoolName>* . 데이터베이스를 성공적으로 복원 하려면 메모리를 더 많이 사용 하 여 메모리 부족 문제를 해결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-119">When you attempt to restore a database you may get the error message: "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'." Before you can successfully restore the database you must resolve the insufficient memory issue by making more memory available.</span></span>  
  
 <span data-ttu-id="2a87c-120">OOM으로 인한 복구 오류를 해결하려면 다음 방법으로 복구 작업에 사용 가능한 메모리를 임시로 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="2a87c-120">To resolve recovery failure due to OOM increase available memory using any or al of these means to temporarily increase memory available for the recovery operation.</span></span>  
  
-   <span data-ttu-id="2a87c-121">실행 중인 애플리케이션을 일시적으로 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-121">Temporarily close running applications.</span></span>   
    <span data-ttu-id="2a87c-122">Visual Studio, Internet Explorer, OneNote 등과 같이 실행 중인 애플리케이션을 하나 이상 닫으면 해당 애플리케이션에서 사용 중인 메모리를 복원 작업에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-122">By closing one or more running applications, such as Visual Studio, Internet Explorer, OneNote, and others, you make the memory they were using available for the restore operation.</span></span> <span data-ttu-id="2a87c-123">성공적으로 복원한 후 해당 응용 프로그램을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-123">You can restart them following the successful restore.</span></span>  
  
-   <span data-ttu-id="2a87c-124">MAX_MEMORY_PERCENT의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-124">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
    <span data-ttu-id="2a87c-125">이 코드 조각은 PoolHk 리소스 풀에 대한 MAX_MEMORY_PERCENT를 설치된 메모리의 70%로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-125">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a87c-126">서버가 VM에서 실행 중이고 전용 서버가 아니면 MIN_MEMORY_PERCENT 값을 MAX_MEMORY_PERCENT와 동일한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-126">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT to the same value as MAX_MEMORY_PERCENT.</span></span>   
    > <span data-ttu-id="2a87c-127">자세한 내용은 [모범 사례: VM 환경에서 메모리 내 OLTP 사용](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-127">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     <span data-ttu-id="2a87c-128">MAX_MEMORY_PERCENT에 대 한 최대값에 대 한 자세한 내용은 [메모리 최적화 테이블 및 인덱스에 사용 가능한 메모리 비율](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes) 항목 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-128">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)</span></span>
  
-   <span data-ttu-id="2a87c-129">**최대 서버 메모리**를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-129">Reconfigure **max server memory**.</span></span>  
    <span data-ttu-id="2a87c-130">**최대 서버 메모리** 구성에 대한 자세한 내용은 [메모리 구성 옵션을 사용하여 서버 성능 최적화](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx)항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-130">For information on configuring **max server memory** see the topic [Optimizing Server Performance Using Memory Configuration Options](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).</span></span>  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a><span data-ttu-id="2a87c-131">메모리 부족 또는 OOM 상황이 작업에 미치는 영향 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-131">Resolve impact of low memory or OOM conditions on the workload</span></span>  
 <span data-ttu-id="2a87c-132">물론 OOM(메모리 부족) 상황에 빠지지 않는 것이 최선입니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-132">Obviously, it is best to not get into a low memory or OOM (Out of Memory) situation.</span></span> <span data-ttu-id="2a87c-133">적절한 계획과 모니터링을 통해 OOM 상황을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-133">Good planning and monitoring can help avoid OOM situations.</span></span> <span data-ttu-id="2a87c-134">그렇지만 최상의 계획을 세우더라도 실제 발생하는 상황을 항상 예측할 수 있는 것은 아니며 결국 메모리 부족 또는 OOM 상황에 도달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-134">Still, the best planning does not always foresee what actually happens and you might end up with low memory or OOM.</span></span> <span data-ttu-id="2a87c-135">다음 두 가지 방법으로 OOM에서 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-135">There are two steps to recovering from OOM:</span></span>  
  
1.  [<span data-ttu-id="2a87c-136">DAC(관리자 전용 연결) 열기</span><span class="sxs-lookup"><span data-stu-id="2a87c-136">Open a DAC (Dedicated Administrator Connection)</span></span>](#open-a-dac-dedicated-administrator-connection) 
  
2.  [<span data-ttu-id="2a87c-137">수정 조치 수행</span><span class="sxs-lookup"><span data-stu-id="2a87c-137">Take corrective action</span></span>](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a><span data-ttu-id="2a87c-138">DAC(관리자 전용 연결) 열기</span><span class="sxs-lookup"><span data-stu-id="2a87c-138">Open a DAC (Dedicated Administrator Connection)</span></span>  
 <span data-ttu-id="2a87c-139">Microsoft SQL Server는 DAC(관리자 전용 연결)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-139">Microsoft SQL Server provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="2a87c-140">DAC를 사용하면 관리자는 서버가 다른 클라이언트 연결에 응답하지 않는 경우에도 실행 중인 SQL Server 데이터베이스 엔진 인스턴스에 액세스하여 서버에서 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-140">The DAC allows an administrator to access a running instance of SQL Server Database Engine to troubleshoot problems on the server-even when the server is unresponsive to other client connections.</span></span> <span data-ttu-id="2a87c-141">DAC는 `sqlcmd` 유틸리티와 SQL Server Management Studio(SSMS)를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-141">The DAC is available through the `sqlcmd` utility and SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="2a87c-142">`sqlcmd` 및 DAC 사용에 대한 지침은 [관리자 전용 연결 사용](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a87c-142">For guidance on using `sqlcmd` and DAC see [Using a Dedicated Administrator Connection](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="2a87c-143">SSMS를 통해 DAC 사용에 대한 지침은 [방법: SQL Server Management Studio에서 관리자 전용 연결 사용](https://msdn.microsoft.com/library/ms178068.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-143">For guidance on using DAC through SSMS see [How to: Use the Dedicated Administrator Connection with SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).</span></span>  
  
### <a name="take-corrective-action"></a><span data-ttu-id="2a87c-144">수정 조치 수행</span><span class="sxs-lookup"><span data-stu-id="2a87c-144">Take corrective action</span></span>  
 <span data-ttu-id="2a87c-145">OOM 상태를 해결하려면 사용을 축소하여 기존 메모리를 확보하거나 더 많은 메모리를 메모리 내 테이블에 사용할 수 있게 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-145">To resolve your OOM condition you need to either free up existing memory by reducing usage, or make more memory available to your in-memory tables.</span></span>  
  
#### <a name="free-up-existing-memory"></a><span data-ttu-id="2a87c-146">기존 메모리 확보</span><span class="sxs-lookup"><span data-stu-id="2a87c-146">Free up existing memory</span></span>  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a><span data-ttu-id="2a87c-147">필수적이지 않은 메모리 액세스에 최적화된 테이블 행을 삭제하고 가비지 수집 대기</span><span class="sxs-lookup"><span data-stu-id="2a87c-147">Delete non-essential memory optimized table rows and wait for garbage collection</span></span>  
 <span data-ttu-id="2a87c-148">메모리 액세스에 최적화된 테이블에서 필수적이지 않은 행을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-148">You can remove non-essential rows from a memory optimized table.</span></span> <span data-ttu-id="2a87c-149">가비지 수집기는 이러한 행에 사용되는 메모리를 사용 가능한 메모리로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-149">The garbage collector returns the memory used by these rows to available memory.</span></span> <span data-ttu-id="2a87c-150">.</span><span class="sxs-lookup"><span data-stu-id="2a87c-150">.</span></span> <span data-ttu-id="2a87c-151">메모리 내 OLTP 엔진은 가비지 행을 적극적으로 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-151">In-memory OLTP engine collects garbage rows aggressively.</span></span> <span data-ttu-id="2a87c-152">그러나 장기 실행 트랜잭션으로 인해 가비지가 수집되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-152">However, a long running transaction can prevent garbage collection.</span></span> <span data-ttu-id="2a87c-153">예를 들어 5분간 실행되는 트랜잭션이 있는 경우 트랜잭션이 활성 상태인 동안 수행되는 업데이트/삭제 작업으로 생성된 모든 행 버전에 대해 가비지가 수집되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-153">For example, if you have a transaction that runs for 5 minutes, any row versions created due to update/delete operations while the transaction was active can't be garbage collected.</span></span>  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a><span data-ttu-id="2a87c-154">디스크 기반 테이블로 하나 이상의 행 이동</span><span class="sxs-lookup"><span data-stu-id="2a87c-154">Move one or more rows to a disk-based table</span></span>  
 <span data-ttu-id="2a87c-155">다음 TechNet 문서에는 메모리 최적화 테이블에서 디스크 기반 테이블로 행을 이동하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-155">The following TechNet articles provide guidance on moving rows from a memory-optimized table to a disk-based table.</span></span>  
  
-   <span data-ttu-id="2a87c-156">[애플리케이션 수준 분할](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2a87c-156">[Application-Level Partitioning](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span></span>  
  
-   <span data-ttu-id="2a87c-157">[메모리 액세스에 최적화된 테이블 분할을 위한 애플리케이션 패턴](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2a87c-157">[Application Pattern for Partitioning Memory-Optimized Tables](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span></span>  
  
#### <a name="increase-available-memory"></a><span data-ttu-id="2a87c-158">사용 가능한 메모리 늘리기</span><span class="sxs-lookup"><span data-stu-id="2a87c-158">Increase available memory</span></span>  
  
##### <a name="increase-value-of-max_memory_percent-on-the-resource-pool"></a><span data-ttu-id="2a87c-159">리소스 풀에서 MAX_MEMORY_PERCENT의 값 늘리기</span><span class="sxs-lookup"><span data-stu-id="2a87c-159">Increase value of MAX_MEMORY_PERCENT on the resource pool</span></span>  
 <span data-ttu-id="2a87c-160">메모리 내 테이블에 대한 명명된 리소스 풀을 만들지 않은 경우 이 리소스 풀을 만들고 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 데이터베이스를 이 리소스 풀에 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-160">If you have not created a named resource pool for your in-memory tables you should do that and bind your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to it.</span></span> <span data-ttu-id="2a87c-161">리소스 풀을 만들고 [데이터베이스를 리소스 풀에 바인딩하는 방법에 대한 지침은](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) 메모리 액세스에 최적화된 테이블이 있는 데이터베이스를 리소스 풀에 바인딩 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-161">See the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) for guidance on creating and binding your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to a resource pool.</span></span>  
  
 <span data-ttu-id="2a87c-162">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 데이터베이스가 리소스 풀에 바인딩된 경우 풀에서 액세스할 수 있는 메모리 비율을 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-162">If your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database is bound to a resource pool you may be able to increase the percent of memory the pool can access.</span></span> <span data-ttu-id="2a87c-163">리소스 풀을 위한 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT의 값 변경에 대한 지침은 하위 항목 [기존 풀에서 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 변경](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-163">See the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) for guidance on changing the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT for a resource pool.</span></span>  
  
 <span data-ttu-id="2a87c-164">MAX_MEMORY_PERCENT의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-164">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
<span data-ttu-id="2a87c-165">이 코드 조각은 PoolHk 리소스 풀에 대한 MAX_MEMORY_PERCENT를 설치된 메모리의 70%로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-165">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a87c-166">서버가 VM에서 실행 중이고 전용 서버가 아니면 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 값을 동일한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-166">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="2a87c-167">자세한 내용은 [모범 사례: VM 환경에서 메모리 내 OLTP 사용](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-167">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="2a87c-168">MAX_MEMORY_PERCENT의 최대값에 대한 자세한 내용은 항목 섹션 [메모리 최적화 테이블 및 인덱스에 사용 가능한 메모리 비율](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-168">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).</span></span>  
  
##### <a name="install-additional-memory"></a><span data-ttu-id="2a87c-169">추가 메모리 설치</span><span class="sxs-lookup"><span data-stu-id="2a87c-169">Install additional memory</span></span>  
 <span data-ttu-id="2a87c-170">가능한 경우 궁극적으로 가장 좋은 해결 방법은 추가 실제 메모리를 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-170">Ultimately the best solution, if possible, is to install additional physical memory.</span></span> <span data-ttu-id="2a87c-171">이렇게 할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 메모리가 더 필요하지 않을 것이므로 MAX_MEMORY_PERCENT 값도 늘려서 새로 설치된 메모리 중 전부는 아니라도 대부분을 리소스 풀에 사용하도록 설정할 수 있습니다(하위 항목 [기존 풀에서 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 변경](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 참조).</span><span class="sxs-lookup"><span data-stu-id="2a87c-171">If you do this, remember that you will probably be able to also increase the value of MAX_MEMORY_PERCENT (see the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)) since [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] won't likely need more memory, allowing you to make most if not all of the newly installed memory available to the resource pool.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a87c-172">서버가 VM에서 실행 중이고 전용 서버가 아니면 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 값을 동일한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-172">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="2a87c-173">자세한 내용은 [모범 사례: VM 환경에서 메모리 내 OLTP 사용](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-173">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a><span data-ttu-id="2a87c-174">사용 가능한 메모리가 충분한 경우 메모리 부족으로 인한 페이지 할당 오류 해결</span><span class="sxs-lookup"><span data-stu-id="2a87c-174">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>  
 <span data-ttu-id="2a87c-175">" *\<databaseName>* ' 리소스 풀의 메모리 부족으로 인해 데이터베이스 ' '에 대 한 페이지 할당을 허용 하지 않습니다." 라는 오류 메시지가 표시 *\<resourcePoolName>* 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-175">If you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="2a87c-176"><https://go.microsoft.com/fwlink/?LinkId=330673>자세한 내용은 ' '를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a87c-176">See '<https://go.microsoft.com/fwlink/?LinkId=330673>' for more information."</span></span> <span data-ttu-id="2a87c-177">라는 오류 메시지가 기록된 경우 리소스 관리자를 사용하지 않기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-177">in the error log when the available physical memory is sufficient to allocate the page, it may be due to a disabled Resource Governor.</span></span> <span data-ttu-id="2a87c-178">리소스 관리자를 사용하지 않으면 MEMORYBROKER_FOR_RESERVE가 인위적인 메모리 압력을 유발합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-178">When the Resource Governor is disabled MEMORYBROKER_FOR_RESERVE induces artificial memory pressure.</span></span>  
  
 <span data-ttu-id="2a87c-179">이 오류를 해결하려면 리소스 관리자를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a87c-179">To resolve this you need to enable the Resource Governor.</span></span>  
  
 <span data-ttu-id="2a87c-180">개체 탐색기, 리소스 관리자 속성 또는 Transact-SQL로 리소스 관리자를 사용하도록 설정하는 지침과 제한 사항에 대한 자세한 내용은 [리소스 관리자 사용](https://technet.microsoft.com/library/bb895149.aspx) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a87c-180">See [Enable Resource Governor](https://technet.microsoft.com/library/bb895149.aspx) for information on Limits and Restrictions as well as guidance on enabling Resource Governor using Object Explorer, Resource Governor properties, or Transact-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a87c-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a87c-181">See Also</span></span>  
 <span data-ttu-id="2a87c-182">[메모리 내 OLTP의 메모리 관리](../../database-engine/managing-memory-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="2a87c-182">[Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="2a87c-183">[메모리 사용량 모니터링 및 문제 해결](monitor-and-troubleshoot-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="2a87c-183">[Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) </span></span>  
 <span data-ttu-id="2a87c-184">[데이터베이스를 리소스 풀에 바인딩하는 방법에 대한 지침은](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="2a87c-184">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 [<span data-ttu-id="2a87c-185">모범 사례: VM 환경에서 메모리 내 OLTP 사용</span><span class="sxs-lookup"><span data-stu-id="2a87c-185">Best Practices: Using In-Memory OLTP in a VM environment</span></span>](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
