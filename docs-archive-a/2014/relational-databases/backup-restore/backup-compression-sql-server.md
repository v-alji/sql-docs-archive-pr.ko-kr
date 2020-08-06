---
title: 백업 압축(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3291a858d8ef037e7cca92eb2e6abb19aec4da8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647071"
---
# <a name="backup-compression-sql-server"></a><span data-ttu-id="9be3f-102">백업 압축(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9be3f-102">Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="9be3f-103">이 항목에서는 제한 사항, 백업 압축이 성능에 미치는 영향, 백업 압축의 구성 및 압축 비율을 비롯하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업의 압축에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-103">This topic describes the compression of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups, including restrictions, performance trade-off of compressing backups, the configuration of backup compression, and the compression ratio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9be3f-104">백업 압축을 지 원하는 버전에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9be3f-104">For information which editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support backup compression, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="9be3f-105">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상의 모든 버전에서는 압축된 백업을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-105">Every edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later can restore a compressed backup.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="9be3f-106">이점</span><span class="sxs-lookup"><span data-stu-id="9be3f-106">Benefits</span></span>  
  
-   <span data-ttu-id="9be3f-107">압축된 백업은 동일한 데이터의 압축되지 않은 백업보다 작으므로 일반적으로 백업 압축에 필요한 디바이스 I/O가 더 적고 따라서 백업 속도가 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-107">Because a compressed backup is smaller than an uncompressed backup of the same data, compressing a backup typically requires less device I/O and therefore usually increases backup speed significantly.</span></span>  
  
     <span data-ttu-id="9be3f-108">자세한 내용은 이 항목 뒷부분의 [백업 압축이 성능에 미치는 영향](#PerfImpact)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9be3f-108">For more information, see [Performance Impact of Compressing Backups](#PerfImpact), later in this topic.</span></span>  
  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9be3f-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9be3f-109">Restrictions</span></span>  
 <span data-ttu-id="9be3f-110">다음은 압축된 백업에 적용되는 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-110">The following restrictions apply to compressed backups:</span></span>  
  
-   <span data-ttu-id="9be3f-111">압축된 백업과 압축되지 않은 백업은 미디어 세트에 동시에 존재할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-111">Compressed and uncompressed backups cannot co-exist in a media set.</span></span>  
  
-   <span data-ttu-id="9be3f-112">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 압축된 백업을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-112">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read compressed backups.</span></span>  
  
-   <span data-ttu-id="9be3f-113">NTbackup은 압축된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업과 테이프를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-113">NTbackups cannot share a tape with compressed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
  
##  <a name="performance-impact-of-compressing-backups"></a><a name="PerfImpact"></a> <span data-ttu-id="9be3f-114">백업 압축이 성능에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="9be3f-114">Performance Impact of Compressing Backups</span></span>  
 <span data-ttu-id="9be3f-115">기본적으로 압축하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-115">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="9be3f-116">따라서 CPU 사용량이[Resource Governor](../resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-116">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="9be3f-117">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-117">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="9be3f-118">백업 I/O 성능을 손쉽게 확인하려면 다음과 같은 성능 카운터를 평가하여 백업 I/O를 디바이스로 격리하거나 디바이스에서 격리하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-118">To obtain a good picture of your backup I/O performance, you can isolate the backup I/O to or from devices by evaluating the following sorts of performance counters:</span></span>  
  
-   <span data-ttu-id="9be3f-119">물리적 디스크 카운터 등의 Windows I/O 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="9be3f-119">Windows I/O performance counters, such as the physical-disk counters</span></span>  
  
-   <span data-ttu-id="9be3f-120">**SQLServer:Backup Device** 개체의 [Device Throughput Bytes/sec](../performance-monitor/sql-server-backup-device-object.md) 카운터</span><span class="sxs-lookup"><span data-stu-id="9be3f-120">The **Device Throughput Bytes/sec** counter of the [SQLServer:Backup Device](../performance-monitor/sql-server-backup-device-object.md) object</span></span>  
  
-   <span data-ttu-id="9be3f-121">**SQLServer:Databases** 개체의 [Backup/Restore Throughput/sec](../performance-monitor/sql-server-databases-object.md) 카운터</span><span class="sxs-lookup"><span data-stu-id="9be3f-121">The **Backup/Restore Throughput/sec** counter of the [SQLServer:Databases](../performance-monitor/sql-server-databases-object.md) object</span></span>  
  
 <span data-ttu-id="9be3f-122">Windows 카운터에 대한 자세한 내용은 Windows 도움말을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9be3f-122">For information about Windows counters, see Windows help.</span></span> <span data-ttu-id="9be3f-123">SQL Server 카운터로 작업하는 방법은 [SQL Server 개체 사용](../performance-monitor/use-sql-server-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9be3f-123">For information about how to work with SQL Server counters, see [Use SQL Server Objects](../performance-monitor/use-sql-server-objects.md).</span></span>  
  
  
##  <a name="calculate-the-compression-ratio-of-a-compressed-backup"></a><a name="CompressionRatio"></a> <span data-ttu-id="9be3f-124">압축된 백업의 압축 비율 계산</span><span class="sxs-lookup"><span data-stu-id="9be3f-124">Calculate the Compression Ratio of a Compressed Backup</span></span>  
 <span data-ttu-id="9be3f-125">백업의 압축 비율을 계산하려면 **backupset** 기록 테이블의 **backup_size** 및 [compressed_backup_size](/sql/relational-databases/system-tables/backupset-transact-sql) 열에서 백업의 값을 다음과 같이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-125">To calculate the compression ratio of a backup, use the values for the backup in the **backup_size** and **compressed_backup_size** columns of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) history table, as follows:</span></span>  
  
 <span data-ttu-id="9be3f-126">**backup_size**:**compressed_backup_size**</span><span class="sxs-lookup"><span data-stu-id="9be3f-126">**backup_size**:**compressed_backup_size**</span></span>  
  
 <span data-ttu-id="9be3f-127">예를 들어 3:1 압축 비율은 디스크 공간을 약 66% 절약할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-127">For example, a 3:1 compression ratio indicates that you are saving about 66% on disk space.</span></span> <span data-ttu-id="9be3f-128">이러한 열에 대해 쿼리하려면 다음 Transact-SQL 문을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-128">To query on these columns, you can use the following Transact-SQL statement:</span></span>  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 <span data-ttu-id="9be3f-129">압축된 백업의 압축 비율은 압축된 데이터에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-129">The compression ratio of a compressed backup depends on the data that has been compressed.</span></span> <span data-ttu-id="9be3f-130">다양한 요소가 결과 압축 비율에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-130">A variety of factors can impact the compression ratio obtained.</span></span> <span data-ttu-id="9be3f-131">주요 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-131">Major factors include:</span></span>  
  
-   <span data-ttu-id="9be3f-132">데이터의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-132">The type of data.</span></span>  
  
     <span data-ttu-id="9be3f-133">문자 데이터는 다른 형식의 데이터보다 압축률이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-133">Character data compresses more than other types of data.</span></span>  
  
-   <span data-ttu-id="9be3f-134">페이지의 행에 포함된 데이터의 일관성</span><span class="sxs-lookup"><span data-stu-id="9be3f-134">The consistency of the data among rows on a page.</span></span>  
  
     <span data-ttu-id="9be3f-135">일반적으로 한 페이지에 필드의 값이 같은 행이 여러 개 있는 경우 이 값에 상당한 압축이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-135">Typically, if a page contains several rows in which a field contains the same value, significant compression might occur for that value.</span></span> <span data-ttu-id="9be3f-136">반면 임의의 데이터가 들어 있거나 페이지당 하나의 큰 행만 들어 있는 데이터베이스의 경우 압축된 백업의 크기가 압축되지 않은 백업의 크기와 거의 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-136">In contrast, for a database that contains random data or that contains only one large row per page, a compressed backup would be almost as large as an uncompressed backup.</span></span>  
  
-   <span data-ttu-id="9be3f-137">데이터의 암호화 여부</span><span class="sxs-lookup"><span data-stu-id="9be3f-137">Whether the data is encrypted.</span></span>  
  
     <span data-ttu-id="9be3f-138">암호화된 데이터는 암호화되지 않은 데이터보다 압축률이 크게 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-138">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="9be3f-139">투명한 데이터 암호화를 사용하여 전체 데이터베이스를 암호화할 경우 백업을 압축해도 크기가 별로 줄어들지 않거나 그대로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-139">If transparent data encryption is used to encrypt an entire database, compressing backups might not reduce their size by much, if at all.</span></span>  
  
-   <span data-ttu-id="9be3f-140">데이터베이스의 압축 여부</span><span class="sxs-lookup"><span data-stu-id="9be3f-140">Whether the database is compressed.</span></span>  
  
     <span data-ttu-id="9be3f-141">데이터베이스가 압축된 경우 백업을 압축하면 크기가 줄어들더라도 많이 줄어들지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-141">If the database is compressed, compressing backups might not reduce their size by much, if at all.</span></span>  
  
  
##  <a name="allocation-of-space-for-the-backup-file"></a><a name="Allocation"></a> <span data-ttu-id="9be3f-142">백업 파일에 대한 공간 할당</span><span class="sxs-lookup"><span data-stu-id="9be3f-142">Allocation of Space for the Backup File</span></span>  
 <span data-ttu-id="9be3f-143">압축된 백업에 대한 최종 백업 파일의 크기는 데이터의 압축 가능한 정도에 따라 달라지며, 백업 작업이 완료되기 전까지는 크기를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-143">For compressed backups, the size of the final backup file depends on how compressible the data is, and this is unknown before the backup operation finishes.</span></span>  <span data-ttu-id="9be3f-144">따라서 기본적으로 압축을 사용하여 데이터베이스를 백업할 때 데이터베이스 엔진은 백업 파일에 대한 사전 할당 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-144">Therefore, by default, when backing up a database using compression, the Database Engine uses a pre-allocation algorithm for the backup file.</span></span> <span data-ttu-id="9be3f-145">이 알고리즘을 사용하면 백업 파일의 데이터베이스 크기에 대해 미리 정의된 백분율이 사전 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-145">This algorithm pre-allocates a predefined percentage of the size of the database for the backup file.</span></span> <span data-ttu-id="9be3f-146">백업하는 동안 더 많은 공간이 필요한 경우 데이터베이스 엔진은 파일을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-146">If more space is needed during the backup operation, the Database Engine grows the file.</span></span> <span data-ttu-id="9be3f-147">백업 작업의 마지막에 최종 크기가 할당된 공간보다 작으면 데이터베이스 엔진이 파일을 백업의 실제 최종 크기로 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-147">If the final size is less than the allocated space, at the end of the backup operation, the Database Engine shrinks the file to the actual final size of the backup.</span></span>  
  
 <span data-ttu-id="9be3f-148">백업 파일을 최종 크기에 도달하는 데 필요한 만큼만 늘리도록 허용하려면 추적 플래그 3042를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-148">To allow the backup file to grow only as needed to reach its final size, use trace flag 3042.</span></span> <span data-ttu-id="9be3f-149">추적 플래그 3042를 사용하면 백업 작업에서 기본 백업 압축 사전 할당 알고리즘을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-149">Trace flag 3042 causes the backup operation to bypass the default backup compression pre-allocation algorithm.</span></span> <span data-ttu-id="9be3f-150">이 추적 플래그는 압축된 백업에 실제로 필요한 크기만 할당하여 공간에 저장해야 하는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9be3f-150">This trace flag is useful if you need to save on space by allocating only the actual size required for the compressed backup.</span></span> <span data-ttu-id="9be3f-151">그러나 이 추적 플래그를 사용하면 약간의 성능 저하가 발생할 수 있습니다(백업 작업 시간이 늘어날 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9be3f-151">However, using this trace flag might cause a slight performance penalty (a possible increase in the duration of the backup operation).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9be3f-152">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9be3f-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9be3f-153">백업 압축 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9be3f-153">Configure Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
-   [<span data-ttu-id="9be3f-154">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="9be3f-154">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [<span data-ttu-id="9be3f-155">Resource Governor를 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9be3f-155">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="9be3f-156">DBCC TRACEON&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9be3f-156">DBCC TRACEON &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [<span data-ttu-id="9be3f-157">DBCC TRACEOFF&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9be3f-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="9be3f-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9be3f-158">See Also</span></span>  
 <span data-ttu-id="9be3f-159">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9be3f-159">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="9be3f-160">추적 플래그&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9be3f-160">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
