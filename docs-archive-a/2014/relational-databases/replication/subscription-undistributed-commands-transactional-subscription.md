---
title: Subscription, 배포 되지 않은 Commands (트랜잭션 구독, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bbd82b4f4855c99076404d8b621edca11a7e1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731504"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a><span data-ttu-id="38599-102">구독, 배포되지 않은 명령(트랜잭션 구독, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="38599-102">Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="38599-103">**배포되지 않은 명령** 탭에는 선택한 구독자에 배달되지 않은 배포 데이터베이스의 명령 수와 해당 명령의 예상 배달 시간에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38599-103">The **Undistributed Commands** tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="38599-104">배포 데이터베이스의 명령을 보는 방법은 [sp_replshowcmds&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38599-104">For information about viewing the commands in the distribution database, see [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="38599-105">옵션</span><span class="sxs-lookup"><span data-stu-id="38599-105">Options</span></span>  
 <span data-ttu-id="38599-106">**이 구독자에 적용되기를 기다리는 배포 데이터베이스의 명령 수**</span><span class="sxs-lookup"><span data-stu-id="38599-106">**Number of commands in the distribution database waiting to be applied to this Subscriber**</span></span>  
 <span data-ttu-id="38599-107">선택한 구독자에 배달되지 않은 배포 데이터베이스의 명령 수.</span><span class="sxs-lookup"><span data-stu-id="38599-107">The number of commands in the distribution database that have not been delivered to the selected Subscriber.</span></span> <span data-ttu-id="38599-108">명령은 하나의 Transact-SQL DML(데이터 조작 언어) 문이나 하나의 DDL(데이터 정의 언어) 문으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="38599-108">A command consists of one Transact-SQL data manipulation language (DML) statement or one data definition language (DDL) statement.</span></span>  
  
 <span data-ttu-id="38599-109">**과거 성능을 기준으로 이 명령 적용에 소요될 예상 시간**</span><span class="sxs-lookup"><span data-stu-id="38599-109">**Estimated time to apply these commands, based on past performance**</span></span>  
 <span data-ttu-id="38599-110">명령을 구독자에 배달하는 데 걸리는 예상 시간.</span><span class="sxs-lookup"><span data-stu-id="38599-110">The estimated amount of time to deliver commands to the Subscriber.</span></span> <span data-ttu-id="38599-111">이 값이 스냅샷을 생성하여 구독자에 적용하는 데 필요한 시간 값보다 더 큰 경우 구독자를 다시 초기화하십시오.</span><span class="sxs-lookup"><span data-stu-id="38599-111">If this value is greater than the amount of time required to generate and apply a snapshot to the Subscriber, consider reinitializing the Subscriber.</span></span> <span data-ttu-id="38599-112">자세한 내용은 [구독 다시 초기화](reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38599-112">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38599-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38599-113">See Also</span></span>  
 <span data-ttu-id="38599-114">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="38599-114">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="38599-115">[복제 모니터를 사용 하 여 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="38599-115">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 [<span data-ttu-id="38599-116">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="38599-116">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
