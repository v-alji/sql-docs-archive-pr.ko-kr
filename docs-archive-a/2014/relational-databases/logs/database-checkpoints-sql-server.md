---
title: 데이터베이스 검사점(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- automatic checkpoints
- transaction logs [SQL Server], checkpoints
- logs [SQL Server], active
- pages [SQL Server], dirty
- MinLSN
- checkpoints [SQL Server]
- pages [SQL Server], flushing
- dirty pages
- transaction logs [SQL Server], active logs
- recovery interval option [SQL Server]
- buffer cache [SQL Server]
- logs [SQL Server], checkpoints
- Minimum Recovery LSN
- flushing pages
- active logs
ms.assetid: 98a80238-7409-4708-8a7d-5defd9957185
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5776d4a23223637c50ac40098fa44342d5cd94a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649539"
---
# <a name="database-checkpoints-sql-server"></a><span data-ttu-id="131f4-102">데이터베이스 검사점(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="131f4-102">Database Checkpoints (SQL Server)</span></span>
  <span data-ttu-id="131f4-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 검사점에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-103">This topic provides an overview of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database checkpoints.</span></span> <span data-ttu-id="131f4-104">*검사점* 은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 예기치 않은 종료 또는 충돌 후 복구하는 과정에서 로그에 포함된 변경 내용의 적용을 시작할 수 있는 알려진 올바른 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-104">A *checkpoint* creates a known good point from which the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] can start applying changes contained in the log during recovery after an unexpected shutdown or crash.</span></span>  
  
  
##  <a name="overview-of-checkpoints"></a><a name="Overview"></a><span data-ttu-id="131f4-105">검사점 개요</span><span class="sxs-lookup"><span data-stu-id="131f4-105">Overview of Checkpoints</span></span>  
 <span data-ttu-id="131f4-106">성능상의 이유로 [!INCLUDE[ssDE](../../includes/ssde-md.md)]은 변경 내용이 있을 때마다 메모리(버퍼 캐시)에서 데이터베이스 페이지를 수정하며 이러한 페이지를 디스크에 기록하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-106">For performance reasons, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] performs modifications to database pages in memory-in the buffer cache-and does not write these pages to disk after every change.</span></span> <span data-ttu-id="131f4-107">대신 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 각 데이터베이스에서 정기적으로 검사점을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-107">Rather, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] periodically issues a checkpoint on each database.</span></span> <span data-ttu-id="131f4-108">*검사점* 은 현재 메모리 내의 수정된 페이지( *더티 페이지*라고 함)와 메모리의 트랜잭션 로그 정보를 디스크에 쓰고 트랜잭션 로그에 대한 정보도 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-108">A *checkpoint* writes the current in-memory modified pages (known as *dirty pages*) and transaction log information from memory to disk and, also, records information about the transaction log.</span></span>  
  
 <span data-ttu-id="131f4-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 자동, 간접, 수동 및 내부와 같은 여러 가지 유형의 검사점이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-109">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] supports several types of checkpoints: automatic, indirect, manual, and internal.</span></span> <span data-ttu-id="131f4-110">다음 표에는 검사점의 유형이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-110">The following table summarizes the types of checkpoints.</span></span>  
  
|<span data-ttu-id="131f4-111">Name</span><span class="sxs-lookup"><span data-stu-id="131f4-111">Name</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="131f4-112">인터페이스</span><span class="sxs-lookup"><span data-stu-id="131f4-112">Interface</span></span>|<span data-ttu-id="131f4-113">Description</span><span class="sxs-lookup"><span data-stu-id="131f4-113">Description</span></span>|  
|----------|----------------------------------|-----------------|  
|<span data-ttu-id="131f4-114">자동</span><span class="sxs-lookup"><span data-stu-id="131f4-114">Automatic</span></span>|<span data-ttu-id="131f4-115">EXEC sp_configure **' `recovery interval` ', ' *`seconds`* '**</span><span class="sxs-lookup"><span data-stu-id="131f4-115">EXEC sp_configure **'`recovery interval`','*`seconds`*'**</span></span>|<span data-ttu-id="131f4-116">서버 구성 옵션에서 제안 하는 상한 시간 제한을 충족 하기 위해 백그라운드에서 자동으로 실행 `recovery interval` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-116">Issued automatically in the background to meet the upper time limit suggested by the `recovery interval` server configuration option.</span></span> <span data-ttu-id="131f4-117">자동 검사점은 완료될 때까지 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-117">Automatic checkpoints run to completion.</span></span>  <span data-ttu-id="131f4-118">자동 검사점은 진행 중인 쓰기 작업의 수와 쓰기 지연 시간이 20밀리초 이상으로 증가할 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 이를 감지하는지 여부에 따라 조절됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-118">Automatic checkpoints are throttled based on the number of outstanding writes and whether the [!INCLUDE[ssDE](../../includes/ssde-md.md)] detects an increase in write latency above 20 milliseconds.</span></span><br /><br /> <span data-ttu-id="131f4-119">자세한 내용은 [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="131f4-119">For more information, see [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="131f4-120">간접</span><span class="sxs-lookup"><span data-stu-id="131f4-120">Indirect</span></span>|<span data-ttu-id="131f4-121">ALTER DATABASE ... TARGET_RECOVERY_TIME **=** _target_recovery_time_ {SECONDS &#124; MINUTES} 설정</span><span class="sxs-lookup"><span data-stu-id="131f4-121">ALTER DATABASE ... SET TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS &#124; MINUTES }</span></span>|<span data-ttu-id="131f4-122">지정된 데이터베이스의 사용자 지정 대상 복구 시간에 맞게 백그라운드에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-122">Issued in the background to meet a user-specified target recovery time for a given database.</span></span> <span data-ttu-id="131f4-123">기본 대상 복구 시간은 0으로, 이 경우 데이터베이스에서 자동 검사점 추론이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-123">The default target recovery time is 0, which causes automatic checkpoint heuristics to be used on the database.</span></span> <span data-ttu-id="131f4-124">ALTER DATABASE을 사용하여 TARGET_RECOVERY_TIME을 0보다 크게 설정한 경우 서버 인스턴스에 대해 지정된 복구 간격 대신 이 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-124">If you have used ALTER DATABASE to set TARGET_RECOVERY_TIME to >0, this value is used, rather than the recovery interval specified for the server instance.</span></span><br /><br /> <span data-ttu-id="131f4-125">자세한 내용은 [데이터베이스의 대상 복구 시간 변경&#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md)서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-125">For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md).</span></span>|  
|<span data-ttu-id="131f4-126">설명서</span><span class="sxs-lookup"><span data-stu-id="131f4-126">Manual</span></span>|<span data-ttu-id="131f4-127">CHECKPOINT [ *checkpoint_duration* ]</span><span class="sxs-lookup"><span data-stu-id="131f4-127">CHECKPOINT [ *checkpoint_duration* ]</span></span>|<span data-ttu-id="131f4-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] CHECKPOINT 명령을 실행할 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-128">Issued when you execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] CHECKPOINT command.</span></span> <span data-ttu-id="131f4-129">수동 검사점은 현재 연결된 데이터베이스에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-129">The manual checkpoint occurs in the current database for your connection.</span></span> <span data-ttu-id="131f4-130">기본적으로 수동 검사점은 완료될 때까지 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-130">By default, manual checkpoints run to completion.</span></span> <span data-ttu-id="131f4-131">또한 자동 검사점의 경우와 동일한 방식으로 조절됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-131">Throttling works the same way as for automatic checkpoints.</span></span>  <span data-ttu-id="131f4-132">필요한 경우 *checkpoint_duration* 매개 변수는 수동 검사점을 완료하는 데 필요한 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-132">Optionally, the *checkpoint_duration* parameter specifies a requested amount of time, in seconds, for the checkpoint to complete.</span></span><br /><br /> <span data-ttu-id="131f4-133">자세한 내용은 [CHECKPOINT&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="131f4-133">For more information, see [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql).</span></span>|  
|<span data-ttu-id="131f4-134">내부</span><span class="sxs-lookup"><span data-stu-id="131f4-134">Internal</span></span>|<span data-ttu-id="131f4-135">없음</span><span class="sxs-lookup"><span data-stu-id="131f4-135">None.</span></span>|<span data-ttu-id="131f4-136">디스크 이미지가 현재 로그 상태와 일치하도록 하는 백업 및 데이터베이스 스냅샷 생성 등의 다양한 서버 작업에 의해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-136">Issued by various server operations such as backup and database-snapshot creation to guarantee that disk images match the current state of the log.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="131f4-137">데이터베이스 관리자는 일부 유형의 검사점에 대해 `-k`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고급 설정 옵션을 사용하여 I/O 하위 시스템의 처리량에 따라 검사점 I/O 동작을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-137">The `-k`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] advanced setup option enables a database administrator to throttle checkpoint I/O behavior based on the throughput of the I/O subsystem for some types of checkpoints.</span></span> <span data-ttu-id="131f4-138">`-k`설치 옵션은 자동 검사점 및 기타 제한 되지 않는지 수동 및 내부 검사점에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-138">The `-k` setup option applies to automatic checkpoints and any otherwise unthrottled manual and internal checkpoints.</span></span>  
  
 <span data-ttu-id="131f4-139">자동, 수동 및 내부 검사점의 경우 데이터베이스 복구 중에는 마지막 검사점 다음에 수정된 내용만 롤포워드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-139">For automatic, manual, and internal checkpoints, only modifications made after the latest checkpoint need to be rolled forward during database recovery.</span></span> <span data-ttu-id="131f4-140">이렇게 하면 데이터베이스를 복구하는 데 필요한 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-140">This reduces the time required to recover a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="131f4-141">커밋되지 않은 장기 실행 트랜잭션의 경우 모든 유형의 검사점에 대해 복구 시간이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-141">Long-running uncommitted transactions increase recovery time for all types of checkpoints.</span></span>  
  
  
  
###  <a name="interaction-of-the-target_recovery_time-and-recovery-interval-options"></a><a name="InteractionBwnSettings"></a> <span data-ttu-id="131f4-142">TARGET_RECOVERY_TIME 옵션과 'recovery interval' 옵션의 상호 작용</span><span class="sxs-lookup"><span data-stu-id="131f4-142">Interaction of the TARGET_RECOVERY_TIME and 'recovery interval' Options</span></span>  
 <span data-ttu-id="131f4-143">다음 표에서는 서버 차원의 **sp_configure ' `recovery interval` '** 설정과 데이터베이스 관련 ALTER database ...의 상호 작용을 요약 하 여 보여 줍니다. TARGET_RECOVERY_TIME 설정.</span><span class="sxs-lookup"><span data-stu-id="131f4-143">The following table summarizes the interaction between the server-wide **sp_configure'`recovery interval`'** setting and the database-specific ALTER DATABASE ... TARGET_RECOVERY_TIME setting.</span></span>  
  
|<span data-ttu-id="131f4-144">target_recovery_time</span><span class="sxs-lookup"><span data-stu-id="131f4-144">TARGET_RECOVERY_TIME</span></span>|<span data-ttu-id="131f4-145">'recovery interval'</span><span class="sxs-lookup"><span data-stu-id="131f4-145">'recovery interval'</span></span>|<span data-ttu-id="131f4-146">사용되는 검사점 유형</span><span class="sxs-lookup"><span data-stu-id="131f4-146">Type of Checkpoint Used</span></span>|  
|----------------------------|-------------------------|-----------------------------|  
|<span data-ttu-id="131f4-147">0</span><span class="sxs-lookup"><span data-stu-id="131f4-147">0</span></span>|<span data-ttu-id="131f4-148">0</span><span class="sxs-lookup"><span data-stu-id="131f4-148">0</span></span>|<span data-ttu-id="131f4-149">대상 복구 간격이 1분인 자동 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-149">automatic checkpoints whose target recovery interval is 1 minute.</span></span>|  
|<span data-ttu-id="131f4-150">0</span><span class="sxs-lookup"><span data-stu-id="131f4-150">0</span></span>|<span data-ttu-id="131f4-151">>0</span><span class="sxs-lookup"><span data-stu-id="131f4-151">>0</span></span>|<span data-ttu-id="131f4-152">대상 복구 간격이 **sp_configure 복구 간격** 옵션의 사용자 정의 설정에 의해 지정되는 자동 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-152">Automatic checkpoints whose target recovery interval is specified by the user defined setting of the **sp_configurerecovery interval** option.</span></span>|  
|<span data-ttu-id="131f4-153">>0</span><span class="sxs-lookup"><span data-stu-id="131f4-153">>0</span></span>|<span data-ttu-id="131f4-154">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="131f4-154">Not applicable.</span></span>|<span data-ttu-id="131f4-155">대상 복구 간격이 TARGET_RECOVERY_TIME 설정에 의해 초 단위로 결정되는 간접 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-155">Indirect checkpoints whose target recovery time is determined by the TARGET_RECOVERY_TIME setting, expressed in seconds.</span></span>|  
  
###  <a name="automatic-checkpoints"></a><a name="AutomaticChkpt"></a><span data-ttu-id="131f4-156">자동 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-156">Automatic Checkpoints</span></span>  
 <span data-ttu-id="131f4-157">자동 검사점은 로그 레코드 수가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서버 구성 옵션에 지정 된 시간 동안 처리할 수 있는 것으로 예상 하는 수에 도달할 때마다 발생 합니다 `recovery interval` .</span><span class="sxs-lookup"><span data-stu-id="131f4-157">An automatic checkpoint occurs each time that  the number of log records reaches the number the [!INCLUDE[ssDE](../../includes/ssde-md.md)] estimates it can process during the time specified in the `recovery interval` server configuration option.</span></span> <span data-ttu-id="131f4-158">사용자 정의 대상 복구 시간이 없는 모든 데이터베이스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 자동 검사점을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-158">In every database without a user-defined target recovery time, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] generates automatic checkpoints.</span></span> <span data-ttu-id="131f4-159">자동 검사점의 빈도는 `recovery interval` 지정 된 서버 인스턴스에서 시스템을 다시 시작 하는 동안 데이터베이스를 복구 하는 데 사용 해야 하는 최대 시간을 지정 하는 고급 서버 구성 옵션에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-159">The frequency of automatic checkpoints depends on the `recovery interval` advanced server configuration option, which specifies the maximum time that a given server instance should use to recover a database during a system restart.</span></span> <span data-ttu-id="131f4-160">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 복구 간격 내에 처리할 수 있는 최대 로그 레코드 수를 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-160">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] estimates the maximum number of log records it can process within the recovery interval.</span></span> <span data-ttu-id="131f4-161">자동 검사점을 사용하는 데이터베이스가 이 최대 로그 레코드 수에 도달하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 데이터베이스에 대해 검사점을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-161">When a database that is using automatic checkpoints reaches this maximum number of log records, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] issues an checkpoint on the database.</span></span> <span data-ttu-id="131f4-162">자동 검사점 사이의 시간 간격은 매우 가변적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-162">The time interval between automatic checkpoints can be highly variable.</span></span> <span data-ttu-id="131f4-163">트랜잭션 작업이 많은 데이터베이스는 읽기 전용 작업에 주로 사용되는 데이터베이스보다 검사점이 더 많습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-163">A database with a substantial transaction workload will have more frequent checkpoints than a database that is used primarily for read-only operations.</span></span>  
  
 <span data-ttu-id="131f4-164">또한 단순 복구 모델에서 자동 검사점은 로그의 70%가 찬 경우에도 큐에 들어갑니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-164">Also, under the simple recovery model, an automatic checkpoint is also queued if the log becomes 70 percent full.</span></span>  
  
 <span data-ttu-id="131f4-165">단순 복구 모델에서는 어떤 요인으로 인해 로그 잘림이 지연되지 않는 한 자동 검사점에 의해 트랜잭션 로그의 사용되지 않는 부분이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-165">Under the simple recovery model, unless some factor is delaying log truncation, an automatic checkpoint truncates the unused section of the transaction log.</span></span> <span data-ttu-id="131f4-166">반면 전체 및 대량 로그 복구 모델에서 로그 백업 체인이 설정된 후에는 자동 검사점에 의해 로그 잘림이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-166">In contrast, under the full and bulk-logged recovery models, once a log backup chain has been established, automatic checkpoints do not cause log truncation.</span></span> <span data-ttu-id="131f4-167">자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](the-transaction-log-sql-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="131f4-167">For more information, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="131f4-168">시스템 충돌이 발생한 후 특정 데이터베이스를 복구하는 데 필요한 시간은 충돌 시 더티 상태였던 페이지를 다시 실행하는 데 필요한 임의 I/O의 양에 따라 크게 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-168">After a system crash, the length of time required to recover a given database is largely dependent on the amount of random I/O needed to redo pages that were dirty at the time of the crash.</span></span> <span data-ttu-id="131f4-169">이는 `recovery interval` 설정이 불안정 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-169">This means that the `recovery interval` setting is unreliable.</span></span> <span data-ttu-id="131f4-170">정확한 복구 기간을 결정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-170">It cannot determine an accurate recovery duration.</span></span> <span data-ttu-id="131f4-171">또한 자동 검사점이 진행 중일 때는 데이터에 대한 일반적인 I/O 작업이 예측할 수 없게 상당히 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-171">Furthermore, when an automatic checkpoint is in progress, the general I/O activity for data increases significantly and quite unpredictably.</span></span>  
  
  
####  <a name="impact-of-recovery-interval-on-recovery-performance"></a><a name="PerformanceImpact"></a><span data-ttu-id="131f4-172">복구 간격이 복구 성능에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="131f4-172">Impact of Recovery Interval on Recovery Performance</span></span>  
 <span data-ttu-id="131f4-173">짧은 트랜잭션을 사용 하는 OLTP (온라인 트랜잭션 처리) 시스템의 경우 `recovery interval` 복구 시간을 결정 하는 기본 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-173">For an online transaction processing (OLTP) system using short transactions, `recovery interval` is the primary factor determining recovery time.</span></span> <span data-ttu-id="131f4-174">그러나이 `recovery interval` 옵션은 장기 실행 트랜잭션을 실행 취소 하는 데 필요한 시간에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-174">However, the `recovery interval` option does not affect the time required to undo a long-running transaction.</span></span> <span data-ttu-id="131f4-175">장기 실행 트랜잭션이 있는 데이터베이스의 복구는 옵션에 지정 된 것 보다 훨씬 더 오래 걸릴 수 있습니다 `recovery interval` .</span><span class="sxs-lookup"><span data-stu-id="131f4-175">Recovery of a database with a long-running transaction can take much longer than the specified in the `recovery interval` option.</span></span> <span data-ttu-id="131f4-176">예를 들어 서버 인스턴스가 비활성화 되기 전에 장기 실행 트랜잭션에서 업데이트를 수행 하는 데 2 시간이 소요 되는 경우 실제 복구는 `recovery interval` 긴 트랜잭션을 복구 하는 값 보다 훨씬 더 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-176">For example, if a long-running transaction took two hours to perform updates before the server instance became disabled, the actual recovery takes considerably longer than the `recovery interval` value to recover the long transaction.</span></span> <span data-ttu-id="131f4-177">장기 실행 트랜잭션이 복구 시간에 미치는 영향에 대한 자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](the-transaction-log-sql-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="131f4-177">For more information about the impact of a long running transaction on recovery time, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="131f4-178">일반적으로 기본값은 최적의 복구 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-178">Typically, the default values provides optimal recovery performance.</span></span> <span data-ttu-id="131f4-179">그러나 다음과 같은 경우에는 복구 간격을 변경하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-179">However, changing the recovery interval might improve performance in the following circumstances:</span></span>  
  
-   <span data-ttu-id="131f4-180">장기 실행 트랜잭션이 롤백되고 있지 않은 상태에서 복구하는 데 통상 1분이 훨씬 넘게 걸리는 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-180">If recovery routinely takes significantly longer than 1 minute when long-running transactions are not being rolled back.</span></span>  
  
-   <span data-ttu-id="131f4-181">검사점이 많아 데이터베이스의 성능이 저하되고 있음을 발견한 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-181">If you notice that frequent checkpoints are impairing performance on a database.</span></span>  
  
 <span data-ttu-id="131f4-182">`recovery interval` 설정을 늘리려는 경우에는 값을 조금씩 늘려가며 그에 따라 복구 성능에 미치는 영향을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-182">If you decide to increase the `recovery interval` setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.</span></span> <span data-ttu-id="131f4-183">`recovery interval`설정이 늘어나면 데이터베이스 복구를 완료 하는 데 시간이 더 오래 걸리므로이 방법이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-183">This approach is important because as the `recovery interval` setting increases, database recovery takes that many times longer to complete.</span></span> <span data-ttu-id="131f4-184">예를 들어 `recovery interval` 10을 변경 하 `recovery interval` 는 경우가 0으로 설정 된 경우 보다 복구를 완료 하는 데 약 10 배 더 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-184">For example, if you change `recovery interval` 10, recovery takes approximately 10 times longer to complete than when `recovery interval` is set to zero.</span></span>  
  
  
###  <a name="indirect-checkpoints"></a><a name="IndirectChkpt"></a><span data-ttu-id="131f4-185">간접 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-185">Indirect Checkpoints</span></span>  
 <span data-ttu-id="131f4-186">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에 새로 추가된 간접 검사점은 자동 검사점 대신 사용할 수 있는 구성 가능한 데이터베이스 수준 검사점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-186">Indirect checkpoints, new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], provide a configurable database-level alternative to automatic checkpoints.</span></span> <span data-ttu-id="131f4-187">시스템이 충돌할 경우 간접 검사점을 사용하면 자동 검사점을 사용할 때보다 복구 시간이 빠르고 보다 예측 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-187">In the event of a system crash, indirect checkpoints provide potentially faster, more predictable recovery time than automatic checkpoints.</span></span> <span data-ttu-id="131f4-188">간접 검사점은 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-188">Indirect checkpoints offer the following advantages:</span></span>  
  
-   <span data-ttu-id="131f4-189">간접 검사점이 구성된 데이터베이스의 온라인 트랜잭션 작업으로 인해 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-189">An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="131f4-190">간접 검사점은 데이터베이스 복구가 대상 복구 시간 내에 완료되도록 더티 페이지 수가 특정 임계값보다 적은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-190">Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time.</span></span> <span data-ttu-id="131f4-191">복구 간격 구성 옵션은 더티 페이지 수를 사용하는 간접 검사점과 달리 트랜잭션 수를 사용하여 복구 시간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-191">The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages.</span></span> <span data-ttu-id="131f4-192">많은 수의 DML 작업을 수신하는 데이터베이스에서 간접 검사점을 사용하도록 설정하는 경우 복구 수행에 필요한 시간이 데이터베이스의 대상 복구 시간 설정 내로 유지되도록 백그라운드 기록기가 더티 버퍼를 디스크로 적극적으로 플러시하기 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-192">When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database.</span></span> <span data-ttu-id="131f4-193">이로 인해 특정 시스템에서 추가 I/O 작업이 발생할 수 있으므로 디스크 하위 시스템이 I/O 임계값 위에서 또는 근처에서 작동하는 경우 성능 병목 현상에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-193">This can cause additional I/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I/O threshold.</span></span>  
  
-   <span data-ttu-id="131f4-194">간접 검사점을 사용하면 REDO 동안의 임의 I/O 비용을 줄여 데이터베이스 복구 시간을 안정적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-194">Indirect checkpoints enable you to reliably control database recovery time by factoring in the cost of random I/O during REDO.</span></span> <span data-ttu-id="131f4-195">이를 통해 서버 인스턴스를 특정 데이터베이스의 복구 시간 상한 내로 유지할 수 있습니다. 장기 실행 트랜잭션으로 인해 UNDO 시간이 과도하게 길어지는 경우에는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-195">This enables a server instance to stay within an upper-bound on recovery times for a given database (except when a long-running transaction causes excessive UNDO times).</span></span>  
  
-   <span data-ttu-id="131f4-196">간접 검사점은 백그라운드에서 더티 페이지를 디스크에 계속 기록하여 검사점 관련 I/O의 급격한 증가를 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-196">Indirect checkpoints reduce checkpoint-related I/O spiking by continually writing dirty pages to disk in the background.</span></span>  
  
 <span data-ttu-id="131f4-197">그러나 간접 검사점이 구성된 데이터베이스의 온라인 트랜잭션 작업으로 인해 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-197">However, an online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="131f4-198">이는 간접 검사점에 사용되는 백그라운드 기록기로 인해 서버 인스턴스에 대한 총 쓰기 부하가 늘어날 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-198">This is because the background writer used by indirect checkpoint sometimes increases the total write load for a server instance.</span></span>  
  
  
###  <a name="internal-checkpoints"></a><a name="EventsCausingChkpt"></a><span data-ttu-id="131f4-199">내부 검사점</span><span class="sxs-lookup"><span data-stu-id="131f4-199">Internal Checkpoints</span></span>  
 <span data-ttu-id="131f4-200">내부 검사점은 디스크 이미지가 현재 로그 상태와 일치하도록 다양한 서버 구성 요소에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-200">Internal Checkpoints are generated by various server components to guarantee that disk images match the current state of the log.</span></span> <span data-ttu-id="131f4-201">내부 검사점은 다음 이벤트에 대한 응답으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-201">Internal checkpoint are generated in response to the following events:</span></span>  
  
-   <span data-ttu-id="131f4-202">ALTER DATABASE를 사용하여 데이터베이스 파일을 추가 또는 제거한 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-202">Database files have been added or removed by using ALTER DATABASE.</span></span>  
  
-   <span data-ttu-id="131f4-203">데이터베이스를 백업한 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-203">A database backup is taken.</span></span>  
  
-   <span data-ttu-id="131f4-204">DBCC CHECK를 위해 명시적으로 또는 내부적으로 데이터베이스 스냅샷이 생성된 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-204">A database snapshot is created, whether explicitly or internally for DBCC CHECK.</span></span>  
  
-   <span data-ttu-id="131f4-205">데이터베이스를 종료해야 하는 작업을 수행한 경우.</span><span class="sxs-lookup"><span data-stu-id="131f4-205">An activity requiring a database shutdown is performed.</span></span> <span data-ttu-id="131f4-206">AUTO_CLOSE가 ON이고 데이터베이스에 대한 마지막 사용자 연결이 닫힌 경우 또는 데이터베이스를 다시 시작해야 하는 데이터베이스 옵션 변경을 수행한 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-206">For example, AUTO_CLOSE is ON and the last user connection to the database is closed, or a database option change is made that requires a restart of the database.</span></span>  
  
-   <span data-ttu-id="131f4-207">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) 서비스를 중지하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 중지된 경우.</span><span class="sxs-lookup"><span data-stu-id="131f4-207">An instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is stopped by stopping the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) service .</span></span> <span data-ttu-id="131f4-208">두 동작은 모두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 각 데이터베이스에 검사점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="131f4-208">Either action  causes a checkpoint in each database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="131f4-209">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FCI(장애 조치(Failover) 클러스터 인스턴스)를 오프라인으로 전환한 경우</span><span class="sxs-lookup"><span data-stu-id="131f4-209">Bringing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance (FCI) offline.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="131f4-210">관련 작업</span><span class="sxs-lookup"><span data-stu-id="131f4-210">Related Tasks</span></span>  
 <span data-ttu-id="131f4-211">**서버 인스턴스의 복구 간격을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="131f4-211">**To change the recovery interval on a server instance**</span></span>  
  
-   [<span data-ttu-id="131f4-212">복구 간격 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="131f4-212">Configure the recovery interval Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)  
  
 <span data-ttu-id="131f4-213">**데이터베이스에 간접 검사점을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="131f4-213">**To configure indirect checkpoints on a database**</span></span>  
  
-   [<span data-ttu-id="131f4-214">데이터베이스의 대상 복구 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="131f4-214">Change the Target Recovery Time of a Database &#40;SQL Server&#41;</span></span>](change-the-target-recovery-time-of-a-database-sql-server.md)  
  
 <span data-ttu-id="131f4-215">**데이터베이스에서 수동 검사점을 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="131f4-215">**To issue a manual checkpoint on a database**</span></span>  
  
-   [<span data-ttu-id="131f4-216">CHECKPOINT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="131f4-216">CHECKPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/checkpoint-transact-sql)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="131f4-217">관련 내용</span><span class="sxs-lookup"><span data-stu-id="131f4-217">Related Content</span></span>  
  
-   <span data-ttu-id="131f4-218">[트랜잭션 로그 물리 아키텍처](https://technet.microsoft.com/library/ms179355.aspx) ( [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 온라인 설명서)</span><span class="sxs-lookup"><span data-stu-id="131f4-218">[Transaction Log Physical Architecture](https://technet.microsoft.com/library/ms179355.aspx) (in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Oline)</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="131f4-219">참고 항목</span><span class="sxs-lookup"><span data-stu-id="131f4-219">See Also</span></span>  
 [<span data-ttu-id="131f4-220">트랜잭션 로그&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="131f4-220">The Transaction Log &#40;SQL Server&#41;</span></span>](the-transaction-log-sql-server.md)  
  
  