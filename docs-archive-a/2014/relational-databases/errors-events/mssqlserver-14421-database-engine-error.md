---
title: MSSQLSERVER_14421 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14421 (Database Engine error)
ms.assetid: 03e76d4a-d463-4673-8843-08e4ecaefe27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d6bc793911797c334d87238ec46531f7afbf63ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653952"
---
# <a name="mssqlserver_14421"></a><span data-ttu-id="4ddf8-102">MSSQLSERVER_14421</span><span class="sxs-lookup"><span data-stu-id="4ddf8-102">MSSQLSERVER_14421</span></span>
    
## <a name="details"></a><span data-ttu-id="4ddf8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4ddf8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ddf8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4ddf8-104">Product Name</span></span>|<span data-ttu-id="4ddf8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4ddf8-105">SQL Server</span></span>|  
|<span data-ttu-id="4ddf8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4ddf8-106">Event ID</span></span>|<span data-ttu-id="4ddf8-107">14421</span><span class="sxs-lookup"><span data-stu-id="4ddf8-107">14421</span></span>|  
|<span data-ttu-id="4ddf8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4ddf8-108">Event Source</span></span>|<span data-ttu-id="4ddf8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4ddf8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4ddf8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4ddf8-110">Component</span></span>|<span data-ttu-id="4ddf8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4ddf8-111">SQLEngine</span></span>|  
|<span data-ttu-id="4ddf8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4ddf8-112">Symbolic Name</span></span>|<span data-ttu-id="4ddf8-113">SQLErrorNum14421</span><span class="sxs-lookup"><span data-stu-id="4ddf8-113">SQLErrorNum14421</span></span>|  
|<span data-ttu-id="4ddf8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4ddf8-114">Message Text</span></span>|<span data-ttu-id="4ddf8-115">로그 전달 보조 데이터베이스 %s.%s은(는) 복원 임계값이 %d분이며 동기화되지 않았습니다. %d분 동안 복원이 수행되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-115">The log shipping secondary database %s.%s has restore threshold of %d minutes and is out of sync. No restore was performed for %d minutes.</span></span> <span data-ttu-id="4ddf8-116">복원 대기 시간은 %d분입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-116">Restored latency is %d minutes.</span></span> <span data-ttu-id="4ddf8-117">에이전트 로그 및 로그 전달 모니터 정보를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-117">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ddf8-118">설명</span><span class="sxs-lookup"><span data-stu-id="4ddf8-118">Explanation</span></span>  
 <span data-ttu-id="4ddf8-119">이 메시지는 로그 전달이 복원 임계값을 초과하여 동기화되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-119">This message indicates that log shipping is out of synchronization beyond the restore threshold.</span></span> <span data-ttu-id="4ddf8-120">복원 임계값은 메시지가 생성되기 전에 복원 작업 간에 경과된 시간(분)입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-120">The restore threshold is the number of minutes that can elapse between restore operations before a message is generated.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="4ddf8-121">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="4ddf8-121">Possible Causes</span></span>  
 <span data-ttu-id="4ddf8-122">이 메시지가 반드시 로그 전달 문제를 나타내는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-122">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="4ddf8-123">대신 이 메시지는 다음 문제 중 하나를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-123">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="4ddf8-124">복원 작업이 실행되고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-124">The restore job is not running.</span></span>  
  
     <span data-ttu-id="4ddf8-125">이는 보조 서버 인스턴스의 SQL Server 에이전트 서비스가 실행되고 있지 않거나 작업이 해제되었거나 작업 일정이 변경되었기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-125">Possible causes of the job not running include the following: the SQL Server Agent service on the secondary server instance is not running, the job is disabled, or the schedule of the job has been changed.</span></span>  
  
-   <span data-ttu-id="4ddf8-126">복원 작업이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-126">The restore job is failing.</span></span>  
  
     <span data-ttu-id="4ddf8-127">복원 폴더 경로가 유효하지 않거나 디스크가 꽉 찼거나 RESTORE 문이 실패할 수 있는 다른 원인으로 인해 작업이 실패했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-127">Possible causes of the job failing include the following: the restore folder path is not valid, the disk is full, or any other reason that the RESTORE statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ddf8-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4ddf8-128">User Action</span></span>  
 <span data-ttu-id="4ddf8-129">이 메시지의 문제를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="4ddf8-129">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="4ddf8-130">SQL Server 에이전트 서비스가 보조 서버 인스턴스에 대해 실행되고 있는지 그리고 이 보조 데이터베이스에 대한 복원 작업이 설정되어 적절한 빈도로 실행되도록 예약되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-130">Make sure that the SQL Server Agent service is running for the secondary server instance and that the restore job for this secondary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="4ddf8-131">보조 서버의 복원 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-131">The restore job on the secondary server might be failing.</span></span> <span data-ttu-id="4ddf8-132">이 경우 원인을 찾을 수 있도록 복원 작업에 대한 작업 기록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-132">In this case, check the job history for the restore job to look for the cause.</span></span>  
  
-   <span data-ttu-id="4ddf8-133">보조 서버 인스턴스에서 실행되는 로그 전달 복원 작업의 경우 **log_shipping_monitor_secondary** 테이블을 업데이트하기 위한 모니터 서버 인스턴스로의 연결이 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-133">The log shipping restore job, which runs on the secondary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_secondary** table.</span></span> <span data-ttu-id="4ddf8-134">이는 모니터 서버 인스턴스와 보조 서버 인스턴스 간의 인증 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-134">This might be caused by an authentication problem between the monitor server instance and the secondary server instance.</span></span>  
  
-   <span data-ttu-id="4ddf8-135">백업 경고 임계값에 잘못된 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-135">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="4ddf8-136">이 값은 복원 작업 빈도의 세 배 이상으로 설정되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-136">Ideally, this value is set to at least three times the frequency of the restore job.</span></span> <span data-ttu-id="4ddf8-137">로그 전달을 구성하여 작동한 후에 복원 작업의 빈도를 변경하는 경우 백업 경고 임계값을 이에 맞게 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-137">If you change the frequency of the restore job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="4ddf8-138">모니터 서버 인스턴스가 오프라인 상태가 된 후 다시 온라인 상태로 돌아오는 경우 경고 메시지 작업이 실행되기 전에는 **log_shipping_monitor_secondary** 테이블이 현재 값으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-138">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_secondary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="4ddf8-139">"보조 데이터베이스에 적용할 수 있는 로그 백업 파일을 찾을 수 없습니다"라는 메시지와 함께 복원 작업이 실행되는 경우 오류 14421이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-139">Error 14421 can be raised when a restore job succeeds with, "Could not find a log backup file that could be applied to secondary database."</span></span> <span data-ttu-id="4ddf8-140">이러한 오류가 발생하면 복원 시간은 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-140">When this occurs, the restore time is not updated.</span></span> <span data-ttu-id="4ddf8-141">이 경우 오류는 복사 작업 문제로 인한 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-141">The cause of the error in this case might be an issue with the copy job.</span></span>  
  
     <span data-ttu-id="4ddf8-142">보조 데이터베이스에 대한 최신 데이터를 사용하여 모니터 테이블을 업데이트하려면 보조 서버 인스턴스에서 **sp_refresh_log_shipping_monitor**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-142">To update the monitor tables with the latest data for the secondary database, run **sp_refresh_log_shipping_monitor** on the secondary server instance.</span></span>  
  
-   <span data-ttu-id="4ddf8-143">보조 인스턴스나 모니터 서버 인스턴스의 날짜 또는 시간이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-143">On the secondary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="4ddf8-144">이로 인해 경고 메시지가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-144">This may also generate alert messages.</span></span> <span data-ttu-id="4ddf8-145">두 서버 인스턴스 중 하나에서 시스템 날짜나 시간이 수정되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-145">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ddf8-146">두 서버 인스턴스의 서로 다른 표준 시간대로 인해 문제가 발생하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddf8-146">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddf8-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ddf8-147">See Also</span></span>  
 <span data-ttu-id="4ddf8-148">[Transact-sql&#41;log_shipping_monitor_secondary &#40;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4ddf8-148">[log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="4ddf8-149">[로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ddf8-149">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="4ddf8-150">[Transact-sql&#41;sp_help_log_shipping_monitor_secondary &#40;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4ddf8-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="4ddf8-151">[Transact-sql&#41;sp_refresh_log_shipping_monitor &#40;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4ddf8-151">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="4ddf8-152">로그 전달 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4ddf8-152">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
