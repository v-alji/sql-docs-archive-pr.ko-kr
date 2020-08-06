---
title: MSSQLSERVER_14420 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a17ab1e2281530b06c9ad27ac2a31672de0681e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649093"
---
# <a name="mssqlserver_14420"></a><span data-ttu-id="a5a2c-102">MSSQLSERVER_14420</span><span class="sxs-lookup"><span data-stu-id="a5a2c-102">MSSQLSERVER_14420</span></span>
    
## <a name="details"></a><span data-ttu-id="a5a2c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a5a2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5a2c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a5a2c-104">Product Name</span></span>|<span data-ttu-id="a5a2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5a2c-105">SQL Server</span></span>|  
|<span data-ttu-id="a5a2c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a5a2c-106">Event ID</span></span>|<span data-ttu-id="a5a2c-107">14420</span><span class="sxs-lookup"><span data-stu-id="a5a2c-107">14420</span></span>|  
|<span data-ttu-id="a5a2c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a5a2c-108">Event Source</span></span>|<span data-ttu-id="a5a2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5a2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5a2c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a5a2c-110">Component</span></span>|<span data-ttu-id="a5a2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a5a2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="a5a2c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a5a2c-112">Symbolic Name</span></span>|<span data-ttu-id="a5a2c-113">SQLErrorNum14420</span><span class="sxs-lookup"><span data-stu-id="a5a2c-113">SQLErrorNum14420</span></span>|  
|<span data-ttu-id="a5a2c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a5a2c-114">Message Text</span></span>|<span data-ttu-id="a5a2c-115">로그 전달 주 데이터베이스 %s.%s은(는) 백업 임계값이 %d분이며 %d분 동안 백업 로그 작업을 수행하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-115">The log shipping primary database %s.%s has backup threshold of %d minutes and has not performed a backup log operation for %d minutes.</span></span> <span data-ttu-id="a5a2c-116">에이전트 로그 및 로그 전달 모니터 정보를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-116">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5a2c-117">설명</span><span class="sxs-lookup"><span data-stu-id="a5a2c-117">Explanation</span></span>  
 <span data-ttu-id="a5a2c-118">로그 전달이 백업 임계값을 초과하여 동기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-118">Log shipping is out of synchronization beyond the backup threshold.</span></span> <span data-ttu-id="a5a2c-119">백업 임계값은 로그 전달 백업 작업 간에 허용되는 시간(분)이며 이 시간이 지나면 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-119">The backup threshold is the number of minutes that are allowed to elapse between log-shipping backup jobs before an alert is generated.</span></span> <span data-ttu-id="a5a2c-120">이 메시지가 반드시 로그 전달 문제를 나타내는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-120">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="a5a2c-121">대신 이 메시지는 다음 문제 중 하나를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-121">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="a5a2c-122">백업 작업이 실행되고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-122">The backup job is not running.</span></span> <span data-ttu-id="a5a2c-123">이는 주 서버 인스턴스의 SQL Server 에이전트 서비스가 실행되고 있지 않거나 작업이 해제되었거나 작업 일정이 변경되었기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-123">Possible causes for this include the following: the SQL Server Agent service on the primary server instance is not running, the job is disabled, or the job's schedule has been changed.</span></span>  
  
-   <span data-ttu-id="a5a2c-124">백업 작업이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-124">The backup job is failing.</span></span> <span data-ttu-id="a5a2c-125">이는 백업 폴더 경로가 유효하지 않거나 디스크가 꽉 찼거나 BACKUP 문이 실패할 수 있는 다른 원인으로 인한 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-125">Possible causes for this include the following: the backup folder path is not valid, the disk is full, or any other reason that the BACKUP statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5a2c-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a5a2c-126">User Action</span></span>  
 <span data-ttu-id="a5a2c-127">이 메시지의 문제를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="a5a2c-127">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="a5a2c-128">SQL Server 에이전트 서비스가 주 서버 인스턴스에 대해 실행되고 있는지 그리고 주 데이터베이스에 대한 백업 작업이 설정되어 적절한 빈도로 실행되도록 예약되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-128">Make sure that the SQL Server Agent service is running for the primary server instance and that the backup job for this primary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="a5a2c-129">주 서버의 백업 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-129">The backup job on the primary server might be failing.</span></span> <span data-ttu-id="a5a2c-130">이 경우 원인을 찾을 수 있도록 백업 작업에 대한 작업 기록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-130">In this case, examine the job history for the backup job to look for the cause.</span></span>  
  
-   <span data-ttu-id="a5a2c-131">주 서버 인스턴스에서 실행되는 로그 전달 백업 작업의 경우 **log_shipping_monitor_primary** 테이블을 업데이트하기 위한 모니터 서버 인스턴스에 대한 연결이 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-131">The log shipping backup job, which runs on the primary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_primary** table.</span></span> <span data-ttu-id="a5a2c-132">이는 모니터 서버 인스턴스와 주 서버 인스턴스 간의 인증 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-132">This could be caused by an authentication problem between the monitor server instance and the primary server instance.</span></span>  
  
-   <span data-ttu-id="a5a2c-133">백업 경고 임계값에 잘못된 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-133">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="a5a2c-134">이 값은 백업 작업 빈도의 세 배 이상으로 설정되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-134">Ideally, this value is set to at least three times the frequency of the backup job.</span></span> <span data-ttu-id="a5a2c-135">로그 전달을 구성하여 작동한 후에 백업 작업의 빈도를 변경하는 경우 백업 경고 임계값을 이에 맞게 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-135">If you change the frequency of the backup job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="a5a2c-136">모니터 서버 인스턴스가 오프라인 상태가 된 후 다시 온라인 상태로 돌아오는 경우 경고 메시지 작업이 실행되기 전에는 **log_shipping_monitor_primary** 테이블이 현재 값으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-136">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_primary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="a5a2c-137">주 데이터베이스에 대한 최신 데이터를 사용하여 모니터 테이블을 업데이트하려면 주 서버 인스턴스에서 **sp_refresh_log_shipping_monitor**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-137">To update the monitor tables with the latest data for the primary database, run **sp_refresh_log_shipping_monitor** on the primary server instance.</span></span>  
  
-   <span data-ttu-id="a5a2c-138">주 서버 인스턴스나 모니터 서버 인스턴스의 날짜 또는 시간이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-138">On the primary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="a5a2c-139">이로 인해 경고 메시지가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-139">This may also generate alert messages.</span></span> <span data-ttu-id="a5a2c-140">두 서버 인스턴스 중 하나에서 시스템 날짜나 시간이 수정되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-140">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a5a2c-141">두 서버 인스턴스의 서로 다른 표준 시간대로 인해 문제가 발생하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5a2c-141">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a2c-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5a2c-142">See Also</span></span>  
 <span data-ttu-id="a5a2c-143">[Transact-sql&#41;log_shipping_monitor_primary &#40;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5a2c-143">[log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="a5a2c-144">[로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a5a2c-144">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="a5a2c-145">[Transact-sql&#41;sp_help_log_shipping_monitor_primary &#40;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5a2c-145">[sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="a5a2c-146">[Transact-sql&#41;sp_refresh_log_shipping_monitor &#40;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5a2c-146">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="a5a2c-147">로그 전달 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a5a2c-147">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
