---
title: 트랜잭션 로그 파일의 크기 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 219ba0605d60bab0b13675f7f9f7ff01cace5755
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649532"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a><span data-ttu-id="c90fe-102">트랜잭션 로그 파일의 크기 관리</span><span class="sxs-lookup"><span data-stu-id="c90fe-102">Manage the Size of the Transaction Log File</span></span>
  <span data-ttu-id="c90fe-103">경우에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 트랜잭션 로그에 대한 실제 로그 파일을 축소하거나 확장하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-103">In some cases, it can be useful to physically shrink or expand the physical log file of the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="c90fe-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 트랜잭션 로그 크기 모니터링, 트랜잭션 로그 축소, 트랜잭션 로그 파일 추가 또는 확장, **tempdb** 트랜잭션 로그 증가율 최적화, 트랜잭션 로그 파일 증가 제어 등을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-104">This topic contains information about how to monitor the size of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, shrink the transaction log, add or enlarge a transaction log file, optimize the **tempdb** transaction log growth rate, and control the growth of a transaction log file.</span></span>  
  
  
##  <a name="monitor-log-space-use"></a><a name="MonitorSpaceUse"></a><span data-ttu-id="c90fe-105">로그 공간 사용 모니터링</span><span class="sxs-lookup"><span data-stu-id="c90fe-105">Monitor Log Space Use</span></span>  
 <span data-ttu-id="c90fe-106">DBCC SQLPERF(LOGSPACE)를 사용하여 로그 공간 사용을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-106">You can monitor log space use by using DBCC SQLPERF (LOGSPACE).</span></span> <span data-ttu-id="c90fe-107">이 명령은 현재 사용된 로그 공간 크기에 대한 정보를 반환하고 트랜잭션 로그 잘림을 수행해야 하는 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-107">This command returns information about the amount of log space currently used and indicates when the transaction log is in need of truncation.</span></span> <span data-ttu-id="c90fe-108">자세한 내용은 [DBCC SQLPERF&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-108">For more information, see [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql).</span></span> <span data-ttu-id="c90fe-109">로그 파일의 현재 크기, 최대 크기 및 파일의 자동 증가 옵션에 대한 정보를 보기 위해 **sys.database_files**에서 해당 로그 파일의 **size**, **max_size** 및 **growth** 열을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-109">For information about the current size of a log file, its maximum size, and the autogrow option for the file, you can also use the **size**, **max_size**, and **growth** columns for that log file in **sys.database_files**.</span></span> <span data-ttu-id="c90fe-110">자세한 내용은 [sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-110">For more information, see [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c90fe-111">로그 디스크를 오버로드하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-111">We recommend that you avoid overloading the log disk.</span></span>  
  
  
##  <a name="shrink-the-size-of-the-log-file"></a><a name="ShrinkSize"></a><span data-ttu-id="c90fe-112">로그 파일 크기 축소</span><span class="sxs-lookup"><span data-stu-id="c90fe-112">Shrink the Size of the Log File</span></span>  
 <span data-ttu-id="c90fe-113">실제 로그 파일의 크기를 줄이려면 로그 파일을 축소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-113">To reduce the physical size of a physical log file, you must shrink the log file.</span></span> <span data-ttu-id="c90fe-114">그러면 트랜잭션 로그 파일에 있는 사용하지 않는 공간이 이후에 필요하지 않은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-114">This is useful if you know that a transaction log file contains unused space that you will not be needing.</span></span> <span data-ttu-id="c90fe-115">로그 파일 축소는 데이터베이스가 온라인 상태이고 최소한 하나의 가상 로그 파일이 비어 있는 경우에만 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-115">Shrinking a log file can occur only while the database is online and, also, at least one virtual log file is free.</span></span> <span data-ttu-id="c90fe-116">경우에 따라 다음에 로그가 잘릴 때까지 로그를 축소하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-116">In some cases, shrinking the log may not be possible until after the next log truncation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90fe-117">장기 실행 트랜잭션과 같이 오랜 시간 동안 가상 로그 파일을 활성 상태로 유지하는 요소가 있으면 로그 축소가 제한되거나 로그를 전혀 축소하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-117">Factors, such as a long-running transaction, that keep virtual log files active for an extended period can restrict log shrinkage or even prevent the log from shrinking at all.</span></span> <span data-ttu-id="c90fe-118">로그 잘림을 지연시킬 수 있는 요소에 대한 자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](the-transaction-log-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-118">For information about factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="c90fe-119">로그 파일을 축소하면 논리 로그 부분이 포함되지 않은 하나 이상의 가상 로그 파일( *비활성 가상 로그 파일*)이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-119">Shrinking a log file removes one or more virtual log files that do not hold any part of the logical log (that is, *inactive virtual log files*).</span></span> <span data-ttu-id="c90fe-120">트랜잭션 로그 파일을 축소하면 대략적인 대상 크기로 로그를 줄이는 데 충분한 개수만큼 비활성 가상 로그 파일이 로그 파일의 끝에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-120">When a transaction log file is shrunk, enough inactive virtual log files are removed from the end of the log file to reduce the log to approximately the target size.</span></span>  
  
 <span data-ttu-id="c90fe-121">**로그 파일을 축소하려면(데이터베이스 파일의 축소 없이)**</span><span class="sxs-lookup"><span data-stu-id="c90fe-121">**To shrink a log file (without shrinking database files)**</span></span>  
  
-   [<span data-ttu-id="c90fe-122">DBCC SHRINKFILE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c90fe-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [<span data-ttu-id="c90fe-123">파일 축소</span><span class="sxs-lookup"><span data-stu-id="c90fe-123">Shrink a File</span></span>](../databases/shrink-a-file.md)  
  
 <span data-ttu-id="c90fe-124">**로그 파일 축소 이벤트를 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="c90fe-124">**To monitor log-file shrink events**</span></span>  
  
-   <span data-ttu-id="c90fe-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).</span></span>  
  
 `To monitor log space`  
  
-   [<span data-ttu-id="c90fe-126">DBCC SQLPERF&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c90fe-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   <span data-ttu-id="c90fe-127">[sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)(로그 파일 또는 파일의 **size**, **max_size** 및 **growth** 열 참조)</span><span class="sxs-lookup"><span data-stu-id="c90fe-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (See the **size**, **max_size**, and **growth** columns for the log file or files.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90fe-128">데이터베이스 및 로그 파일 축소는 자동으로 발생하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-128">Shrinking database and log files can be set to occur automatically.</span></span> <span data-ttu-id="c90fe-129">그러나 자동 축소는 사용하지 않는 것이 좋으며 `autoshrink` 데이터베이스 속성도 기본적으로 FALSE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-129">However, we recommend against automatic shrinking, and the `autoshrink` database property is set to FALSE by default.</span></span> <span data-ttu-id="c90fe-130">`autoshrink`를 TRUE로 설정하면 파일 공간의 25% 이상이 사용되지 않을 때만 자동 축소에 의해 파일 크기가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-130">If `autoshrink` is set to TRUE, automatic shrinking reduces the size of a file only when more than 25 percent of its space is unused.</span></span> <span data-ttu-id="c90fe-131">파일은 파일의 25%만 사용되지 않을 때의 크기 또는 파일의 원래 크기 중 더 큰 크기로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-131">The file is shrunk either to the size at which only 25 percent of the file is unused space or to the original size of the file, whichever is larger.</span></span> <span data-ttu-id="c90fe-132">속성의 설정을 변경 하는 방법에 대 한 자세한 내용은 `autoshrink` [데이터베이스 속성 보기 또는 변경](../databases/view-or-change-the-properties-of-a-database.md)- **옵션** 페이지에서 **자동 축소** 속성 사용-또는 [ALTER database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-AUTO_SHRINK 옵션 사용을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-132">For information about changing the setting of the `autoshrink` property, see [View or Change the Properties of a Database](../databases/view-or-change-the-properties-of-a-database.md)-use the **Auto Shrink** property on the **Options** page-or [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-use the AUTO_SHRINK option.</span></span>  
  
  
##  <a name="add-or-enlarge-a-log-file"></a><a name="AddOrEnlarge"></a><span data-ttu-id="c90fe-133">로그 파일 추가 또는 확장</span><span class="sxs-lookup"><span data-stu-id="c90fe-133">Add or Enlarge a Log File</span></span>  
 <span data-ttu-id="c90fe-134">또는 디스크 공간이 충분한 경우 기존의 로그 파일을 확장하거나 데이터베이스에 일반적으로 다른 디스크에 있는 로그 파일을 추가하여 공간을 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-134">Alternatively, you can gain space by enlarging the existing log file (if disk space permits) or by adding a log file to the database, typically on a different disk.</span></span>  
  
-   <span data-ttu-id="c90fe-135">데이터베이스에 로그 파일을 추가하려면 ALTER DATABASE 문의 ADD LOG FILE 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-135">To add a log file to the database, use the ADD LOG FILE clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="c90fe-136">로그 파일을 추가하면 로그가 확장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-136">Adding a log file allows the log to grow.</span></span>  
  
-   <span data-ttu-id="c90fe-137">로그 파일을 확장하려면 SIZE 및 MAXSIZE 구문을 지정하여 ALTER DATABASE 문의 MODIFY FILE 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-137">To enlarge the log file, use the MODIFY FILE clause of the ALTER DATABASE statement, specifying the SIZE and MAXSIZE syntax.</span></span> <span data-ttu-id="c90fe-138">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-138">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
  
##  <a name="optimize-the-size-of-the-tempdb-transaction-log"></a><a name="tempdbOptimize"></a><span data-ttu-id="c90fe-139">Tempdb 트랜잭션 로그 크기 최적화</span><span class="sxs-lookup"><span data-stu-id="c90fe-139">Optimize the Size of the tempdb Transaction Log</span></span>  
 <span data-ttu-id="c90fe-140">서버 인스턴스를 다시 시작하면 **tempdb** 데이터베이스의 트랜잭션 로그가 자동 증가 이전의 원래 크기로 다시 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-140">Restarting a server instance resizes the transaction log of the **tempdb** database to its original, pre-autogrow size.</span></span> <span data-ttu-id="c90fe-141">이 경우 **tempdb** 트랜잭션 로그의 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-141">This can reduce the performance of the **tempdb** transaction log.</span></span> <span data-ttu-id="c90fe-142">서버 인스턴스를 시작하거나 다시 시작한 후에 **tempdb** 트랜잭션 로그의 크기를 늘려 이 오버헤드를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-142">You can avoid this overhead by increasing the size of the **tempdb** transaction log after starting or restarting the server instance.</span></span> <span data-ttu-id="c90fe-143">자세한 내용은 [tempdb Database](../databases/tempdb-database.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-143">For more information, see [tempdb Database](../databases/tempdb-database.md).</span></span>  
  
  
##  <a name="control-the-growth-of-a-transaction-log-file"></a><a name="ControlGrowth"></a><span data-ttu-id="c90fe-144">트랜잭션 로그 파일의 증가를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-144">Control the Growth of a Transaction Log File</span></span>  
 <span data-ttu-id="c90fe-145">트랜잭션 로그 파일의 증가를 관리하기 위해 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-145">You can use the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement to manage the growth of a transaction log file.</span></span> <span data-ttu-id="c90fe-146">다음 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-146">Note the following:</span></span>  
  
-   <span data-ttu-id="c90fe-147">현재 파일의 크기(KB, MB, GB 및 TB 단위)를 변경하려면 SIZE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-147">To change the current file size in KB, MB, GB, and TB units, use the SIZE option.</span></span>  
  
-   <span data-ttu-id="c90fe-148">증분을 변경하려면 FILEGROWTH 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-148">To change the growth increment, use the FILEGROWTH option.</span></span> <span data-ttu-id="c90fe-149">값 0은 자동 증가를 사용하지 않고 추가 공간을 허용하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-149">A value of 0 indicates that automatic growth is set to off and no additional space is permitted.</span></span> <span data-ttu-id="c90fe-150">로그 파일의 자동 증가분이 적어도 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-150">A small autogrowth increment on a log file can reduce performance.</span></span> <span data-ttu-id="c90fe-151">로그 파일의 파일 증가분이 충분히 커야 자주 확장하는 번거로움을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-151">The file growth increment on a log file should be sufficiently large to avoid frequent expansion.</span></span> <span data-ttu-id="c90fe-152">대개 기본 증가분인 10%가 알맞습니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-152">The default growth increment of 10 percent is generally suitable.</span></span>  
  
     <span data-ttu-id="c90fe-153">로그 파일의 파일 증가 속성을 변경 하는 방법에 대 한 자세한 내용은 [ALTER database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c90fe-153">For information on changing the file-growth property on a log file, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="c90fe-154">로그 파일의 최대 크기(KB, MB, GB 및 TB 단위)를 제어하거나 증가를 UNLIMITED로 설정하려면 MAXSIZE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90fe-154">To control the maximum the size of a log file in KB, MB, GB, and TB units or to set growth to UNLIMITED, use the MAXSIZE option.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="c90fe-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c90fe-155">See Also</span></span>  
 <span data-ttu-id="c90fe-156">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c90fe-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="c90fe-157">꽉 찬 트랜잭션 로그 문제 해결&#40;SQL Server 오류 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="c90fe-157">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
