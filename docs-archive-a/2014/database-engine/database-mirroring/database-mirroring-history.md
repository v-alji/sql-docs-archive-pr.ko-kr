---
title: 데이터베이스 미러링 기록 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e32ad9bfdce15413d89fbd5ba3d79a5ef14f7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653507"
---
# <a name="database-mirroring-history"></a><span data-ttu-id="68e01-102">데이터베이스 미러링 기록</span><span class="sxs-lookup"><span data-stu-id="68e01-102">Database Mirroring History</span></span>
  <span data-ttu-id="68e01-103">이 대화 상자를 사용하여 지정된 서버 인스턴스의 미러링된 데이터베이스에 대한 미러링 상태 기록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-103">Use this dialog box to view the history of mirroring status for a mirrored database on a specified server instance.</span></span>  
  
 <span data-ttu-id="68e01-104">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="68e01-104">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="68e01-105">데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="68e01-105">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="68e01-106">옵션</span><span class="sxs-lookup"><span data-stu-id="68e01-106">Options</span></span>  
 <span data-ttu-id="68e01-107">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="68e01-107">**Server instance**</span></span>  
 <span data-ttu-id="68e01-108">기록이 보고되고 있는 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-108">Name of the server instance from which the history is being reported.</span></span>  
  
 <span data-ttu-id="68e01-109">**Database**</span><span class="sxs-lookup"><span data-stu-id="68e01-109">**Database**</span></span>  
 <span data-ttu-id="68e01-110">해당 기록이 보고되고 있는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-110">Name of the database whose history is being reported.</span></span>  
  
 <span data-ttu-id="68e01-111">**목록 필터 기준**</span><span class="sxs-lookup"><span data-stu-id="68e01-111">**Filter list by**</span></span>  
 <span data-ttu-id="68e01-112">필터 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-112">Lists filter values.</span></span> <span data-ttu-id="68e01-113">새 값을 선택하면 표가 자동으로 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-113">Choosing a new value refreshes the grid automatically.</span></span>  
  
 <span data-ttu-id="68e01-114">가능한 필터 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-114">The possible filter values are:</span></span>  
  
-   <span data-ttu-id="68e01-115">마지막 2시간</span><span class="sxs-lookup"><span data-stu-id="68e01-115">Last two hours</span></span>  
  
-   <span data-ttu-id="68e01-116">마지막 4시간</span><span class="sxs-lookup"><span data-stu-id="68e01-116">Last four hours</span></span>  
  
-   <span data-ttu-id="68e01-117">마지막 8시간</span><span class="sxs-lookup"><span data-stu-id="68e01-117">Last eight hours</span></span>  
  
-   <span data-ttu-id="68e01-118">마지막 1일</span><span class="sxs-lookup"><span data-stu-id="68e01-118">Last day</span></span>  
  
-   <span data-ttu-id="68e01-119">마지막 2일</span><span class="sxs-lookup"><span data-stu-id="68e01-119">Last two days</span></span>  
  
-   <span data-ttu-id="68e01-120">마지막 100개의 레코드</span><span class="sxs-lookup"><span data-stu-id="68e01-120">Last 100 records</span></span>  
  
-   <span data-ttu-id="68e01-121">마지막 500개의 레코드</span><span class="sxs-lookup"><span data-stu-id="68e01-121">Last 500 records</span></span>  
  
-   <span data-ttu-id="68e01-122">마지막 1000개의 레코드</span><span class="sxs-lookup"><span data-stu-id="68e01-122">Last 1000 records</span></span>  
  
-   <span data-ttu-id="68e01-123">모든 레코드</span><span class="sxs-lookup"><span data-stu-id="68e01-123">All records</span></span>  
  
 <span data-ttu-id="68e01-124">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="68e01-124">**Refresh**</span></span>  
 <span data-ttu-id="68e01-125">기록 목록을 새로 고치려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-125">Click to refresh the history list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68e01-126">이 대화 상자는 기록 목록을 자동으로 새로 고치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-126">This dialog box does not automatically refresh the history list.</span></span> <span data-ttu-id="68e01-127">목록을 새로 고치려면 **새로 고침** 을 클릭하거나 다른 필터 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-127">To refresh the list, either click **Refresh** or choose another filter option.</span></span> <span data-ttu-id="68e01-128">**sysadmin** 고정 서버 역할의 멤버만 미러링 기록을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-128">Only members of the **sysadmin** fixed server role can update the mirroring history.</span></span>  
  
 <span data-ttu-id="68e01-129">**History**</span><span class="sxs-lookup"><span data-stu-id="68e01-129">**History**</span></span>  
 <span data-ttu-id="68e01-130">기록 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-130">Displays the history list.</span></span> <span data-ttu-id="68e01-131">열 머리글을 클릭하면 해당 열을 기준으로 표가 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-131">Clicking on a column header sorts the grid by that column.</span></span> <span data-ttu-id="68e01-132">목록에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-132">The list contains the following columns:</span></span>  
  
|<span data-ttu-id="68e01-133">열 이름</span><span class="sxs-lookup"><span data-stu-id="68e01-133">Column name</span></span>|<span data-ttu-id="68e01-134">Description</span><span class="sxs-lookup"><span data-stu-id="68e01-134">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="68e01-135">**기록된 시간**</span><span class="sxs-lookup"><span data-stu-id="68e01-135">**Time Recorded**</span></span>|<span data-ttu-id="68e01-136">기록 행의 타임스탬프입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-136">Timestamp of the history row.</span></span>|  
|<span data-ttu-id="68e01-137">**역할**</span><span class="sxs-lookup"><span data-stu-id="68e01-137">**Role**</span></span>|<span data-ttu-id="68e01-138">이 데이터베이스에 대한 서버 인스턴스의 현재 미러링 역할(주 서버 또는 미러 서버)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-138">Current mirroring role of the server instance for this database, either Principal or Mirror.</span></span>|  
|<span data-ttu-id="68e01-139">**미러링 상태**</span><span class="sxs-lookup"><span data-stu-id="68e01-139">**Mirroring State**</span></span>|<span data-ttu-id="68e01-140">데이터베이스의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-140">State of the database:</span></span><br /><br /> <span data-ttu-id="68e01-141">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="68e01-141">Disconnected</span></span><br /><br /> <span data-ttu-id="68e01-142">장애 조치(Failover) 보류 중</span><span class="sxs-lookup"><span data-stu-id="68e01-142">Pending Failover</span></span><br /><br /> <span data-ttu-id="68e01-143">일시 중단</span><span class="sxs-lookup"><span data-stu-id="68e01-143">Suspended</span></span><br /><br /> <span data-ttu-id="68e01-144">동기화됨</span><span class="sxs-lookup"><span data-stu-id="68e01-144">Synchronized</span></span><br /><br /> <span data-ttu-id="68e01-145">동기화 중</span><span class="sxs-lookup"><span data-stu-id="68e01-145">Synchronizing</span></span><br /><br /> <span data-ttu-id="68e01-146">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="68e01-146">Unknown</span></span>|  
|<span data-ttu-id="68e01-147">**미러링 모니터 서버 연결**</span><span class="sxs-lookup"><span data-stu-id="68e01-147">**Witness Connection**</span></span>|<span data-ttu-id="68e01-148">데이터베이스의 미러링 세션에 있는 미러링 모니터 서버 연결의 상태입니다(연결됨 또는 연결 끊김).</span><span class="sxs-lookup"><span data-stu-id="68e01-148">State of the witness connection in the mirroring session of the database, either Connected or Disconnected.</span></span> <span data-ttu-id="68e01-149">미러링 모니터 서버가 없을 경우 값은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-149">If there is no witness, the value is NULL.</span></span>|  
|<span data-ttu-id="68e01-150">**보내지 않은 로그**</span><span class="sxs-lookup"><span data-stu-id="68e01-150">**Unsent Log**</span></span>|<span data-ttu-id="68e01-151">주 서버 인스턴스의 Send Queue에 있는 보내지 않은 로그의 크기(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-151">Size, in kilobytes (KB), of the unsent log in the send queue on the principal server instance.</span></span>|  
|<span data-ttu-id="68e01-152">**전송 시간**</span><span class="sxs-lookup"><span data-stu-id="68e01-152">**Time to Send**</span></span>|<span data-ttu-id="68e01-153">주 서버 인스턴스에서 현재 Send Queue에 있는 로그를 미러 서버 인스턴스에 보내는 데 필요한 대략적인 시간입니다( *전송 속도*).</span><span class="sxs-lookup"><span data-stu-id="68e01-153">Approximate amount of time the principal server instance will require to send the log that is currently in the send queue to the mirror server instance (the *send rate*).</span></span> <span data-ttu-id="68e01-154">들어오는 트랜잭션의 속도가 크게 달라질 수 있으므로 로그 전송 시간은 예상 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-154">Because the rate of incoming transactions can vary significantly, the time to send log is an estimate.</span></span> <span data-ttu-id="68e01-155">그러나 전송 속도는 수동 장애 조치에 필요한 대략적인 시간을 예상하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-155">However, the send rate can be useful for roughly estimating the time required for a manual failover.</span></span>|  
|<span data-ttu-id="68e01-156">**Send Rate**</span><span class="sxs-lookup"><span data-stu-id="68e01-156">**Send Rate**</span></span>|<span data-ttu-id="68e01-157">트랜잭션이 미러 서버 인스턴스로 전송되는 속도(KB/초)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-157">Rate at which transactions are being sent to the mirror server instance, in KB per second.</span></span>|  
|<span data-ttu-id="68e01-158">**새 트랜잭션 속도**</span><span class="sxs-lookup"><span data-stu-id="68e01-158">**New Transaction Rate**</span></span>|<span data-ttu-id="68e01-159">들어오는 트랜잭션이 주 서버의 로그에 들어오는 속도(KB/초)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-159">Rate at which incoming transactions are being entered into the principal's log, in KB per second.</span></span> <span data-ttu-id="68e01-160">미러링 속도가 늦는지, 보통인지 또는 빠른지를 확인하려면 이 값을 **전송 시간** 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-160">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Time to Send** value.</span></span>|  
|<span data-ttu-id="68e01-161">**보내지 않은 가장 오래된 트랜잭션**</span><span class="sxs-lookup"><span data-stu-id="68e01-161">**Oldest Unsent Transaction**</span></span>|<span data-ttu-id="68e01-162">Send Queue에 있는 보내지 않은 가장 오래된 트랜잭션의 보존 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-162">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="68e01-163">이 트랜잭션의 보존 기간은 트랜잭션이 미러 서버 인스턴스에 전송되지 않은 채로 경과된 시간(분)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-163">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="68e01-164">이 값은 시간을 기준으로 발생 가능한 데이터 손실을 측정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-164">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="68e01-165">**복원되지 않은 로그**</span><span class="sxs-lookup"><span data-stu-id="68e01-165">**Unrestored Log**</span></span>|<span data-ttu-id="68e01-166">Redo Queue에서 대기 중인 로그의 양(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-166">The amount of log waiting in the redo queue, in KB.</span></span>|  
|<span data-ttu-id="68e01-167">**복원 시간**</span><span class="sxs-lookup"><span data-stu-id="68e01-167">**Time to Restore**</span></span>|<span data-ttu-id="68e01-168">현재 Redo Queue에 있는 로그를 미러 데이터베이스에 적용하는 데 필요한 대략적인 시간(분)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-168">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>|  
|<span data-ttu-id="68e01-169">**복원 속도**</span><span class="sxs-lookup"><span data-stu-id="68e01-169">**Restore Rate**</span></span>|<span data-ttu-id="68e01-170">트랜잭션이 미러 데이터베이스로 복원되는 속도(KB/초)입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-170">Rate at which transactions are being restored into the mirror database, in KB per second.</span></span>|  
|<span data-ttu-id="68e01-171">**미러 커밋 오버헤드**</span><span class="sxs-lookup"><span data-stu-id="68e01-171">**Mirror Commit Overhead**</span></span>|<span data-ttu-id="68e01-172">트랜잭션당 평균 지연 시간(밀리초)입니다(동기 모드에만 해당).</span><span class="sxs-lookup"><span data-stu-id="68e01-172">Average delay per transaction in milliseconds (only in synchronous modes).</span></span> <span data-ttu-id="68e01-173">이 지연 시간은 주 서버 인스턴스에서 미리 서버 인스턴스가 트랜잭션 로그 레코드를 Redo Queue에 쓸 때까지 대기하는 동안 발생한 오버헤드 양입니다.</span><span class="sxs-lookup"><span data-stu-id="68e01-173">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68e01-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68e01-174">See Also</span></span>  
 <span data-ttu-id="68e01-175">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="68e01-175">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="68e01-176">[데이터베이스 미러링 모니터링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68e01-176">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="68e01-177">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="68e01-177">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
