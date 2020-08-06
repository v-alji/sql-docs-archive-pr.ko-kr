---
title: SQL Server, Broker Activation 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4048c2baecaeb4bde7a1e215a15e8c51a60a01bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731555"
---
# <a name="sql-server-broker-activation-object"></a><span data-ttu-id="5c7cb-102">SQL Server, Broker 활성화 개체</span><span class="sxs-lookup"><span data-stu-id="5c7cb-102">SQL Server, Broker Activation Object</span></span>
  <span data-ttu-id="5c7cb-103">**SQLServer:BrokerActivation** 성능 개체에는 저장 프로시저 활성화에 대한 정보를 보고하는 성능 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-103">The **SQLServer:BrokerActivation** performance object contains performance counters that report information on stored procedure activation.</span></span> <span data-ttu-id="5c7cb-104">다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-104">The table below lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="5c7cb-105">SQL Server, Broker 활성화 카운터</span><span class="sxs-lookup"><span data-stu-id="5c7cb-105">SQL Server Broker Activation counters</span></span>|<span data-ttu-id="5c7cb-106">Description</span><span class="sxs-lookup"><span data-stu-id="5c7cb-106">Description</span></span>|  
|-------------------------------------------|-----------------|  
|<span data-ttu-id="5c7cb-107">**Stored Procedures Invoked/sec**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-107">**Stored Procedures Invoked/sec**</span></span>|<span data-ttu-id="5c7cb-108">이 카운터는 인스턴스의 모든 큐 모니터에서 호출하는 초당 총 활성화 저장 프로시저 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-108">This counter reports the total number of activation stored procedures invoked by all queue monitors in the instance per second.</span></span>|  
|<span data-ttu-id="5c7cb-109">**Task Limit Reached**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-109">**Task Limit Reached**</span></span>|<span data-ttu-id="5c7cb-110">이 카운터는 큐 모니터가 새 태스크를 시작했지만 해당 큐에 대한 최대 수의 작업이 이미 실행 중이기 때문에 시작하지 못한 총 횟수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-110">This counter reports the total number of times that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="5c7cb-111">**Task Limit Reached/sec**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-111">**Task Limit Reached/sec**</span></span>|<span data-ttu-id="5c7cb-112">이 카운터는 큐 모니터가 새 태스크를 시작했지만 해당 큐에 대한 최대 수의 작업이 이미 실행 중이기 때문에 시작하지 못한 초당 횟수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-112">This counter reports the number of times per second that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="5c7cb-113">**Tasks Aborted/sec**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-113">**Tasks Aborted/sec**</span></span>|<span data-ttu-id="5c7cb-114">이 카운터는 오류로 인해 종료되거나 메시지를 받는 데 실패하여 큐 모니터에서 중단시킨 활성화 저장 프로시저 태스크 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-114">This counter reports the number of activation stored procedure tasks that end with an error, or are aborted by a queue monitor for failing to receive messages.</span></span>|  
|<span data-ttu-id="5c7cb-115">**Tasks Running**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-115">**Tasks Running**</span></span>|<span data-ttu-id="5c7cb-116">이 카운터는 현재 실행 중인 활성화 저장 프로시저 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-116">This counter reports the number of activation stored procedures that are currently running.</span></span>|  
|<span data-ttu-id="5c7cb-117">**Tasks Started/sec**</span><span class="sxs-lookup"><span data-stu-id="5c7cb-117">**Tasks Started/sec**</span></span>|<span data-ttu-id="5c7cb-118">이 카운터는 인스턴스의 모든 큐 모니터에서 시작하는 초당 활성화 저장 프로시저 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7cb-118">This counter reports the number of activation stored procedures started per second by all queue monitors in the instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c7cb-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c7cb-119">See Also</span></span>  
 <span data-ttu-id="5c7cb-120">[sys.dm_broker_activated_tasks&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c7cb-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span></span>  
 <span data-ttu-id="5c7cb-121">[sys.dm_broker_queue_monitors&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c7cb-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span></span>  
 [<span data-ttu-id="5c7cb-122">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="5c7cb-122">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
