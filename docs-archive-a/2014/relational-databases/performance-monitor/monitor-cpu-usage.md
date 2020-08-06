---
title: CPU 사용량 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], CPU usage
- tuning databases [SQL Server], CPU usage
- processors [SQL Server], monitoring usage
- database performance [SQL Server], CPU usage
- monitoring CPU usage [SQL Server]
- server performance [SQL Server], CPU usage
- database monitoring [SQL Server], CPU usage
- monitoring [SQL Server], CPU usage
- processors [SQL Server]
- CPU [SQL Server], monitoring
- monitoring server performance [SQL Server], CPU usage
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f08d49348fd25593f27a87f2b0123f7ce43e35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739748"
---
# <a name="monitor-cpu-usage"></a><span data-ttu-id="5ef3b-102">CPU 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="5ef3b-102">Monitor CPU Usage</span></span>
  <span data-ttu-id="5ef3b-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 정기적으로 모니터링하여 CPU 사용량이 정상 범위에 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-103">Monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to determine whether CPU usage rates are within normal ranges.</span></span> <span data-ttu-id="5ef3b-104">CPU 사용량이 계속 높게 나타나면 CPU 업그레이드 또는 멀티 프로세서 추가가 필요하거나</span><span class="sxs-lookup"><span data-stu-id="5ef3b-104">A continually high rate of CPU usage may indicate the need to upgrade the CPU or add multiple processors.</span></span> <span data-ttu-id="5ef3b-105">애플리케이션 튜닝 또는 디자인이 적절하지 않다는 의미일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-105">Alternatively, a high CPU usage rate may indicate a poorly tuned or designed application.</span></span> <span data-ttu-id="5ef3b-106">애플리케이션을 최적화하면 CPU 사용률을 낮출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-106">Optimizing the application can lower CPU utilization.</span></span>  
  
 <span data-ttu-id="5ef3b-107">CPU 사용량을 확인하는 효과적인 방법은 시스템 모니터의 **Processor:% Processor Time** 카운터를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-107">An efficient way to determine CPU usage is to use the **Processor:% Processor Time** counter in System Monitor.</span></span> <span data-ttu-id="5ef3b-108">카운터는 CPU가 비유휴 스레드를 실행하는 데 소비하는 시간을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-108">This counter monitors the amount of time the CPU spends executing a thread that is not idle.</span></span> <span data-ttu-id="5ef3b-109">카운터 값이 계속 80-90%로 나타나면 CPU를 업그레이드하거나 프로세서를 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-109">A consistent state of 80 percent to 90 percent may indicate the need to upgrade your CPU or add more processors.</span></span> <span data-ttu-id="5ef3b-110">다중 프로세서 시스템에서는 각 프로세서에 대해 이 카운터의 개별 인스턴스를 모니터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-110">For multiprocessor systems, monitor a separate instance of this counter for each processor.</span></span> <span data-ttu-id="5ef3b-111">이 값은 특정 프로세서의 프로세서 시간의 합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-111">This value represents the sum of processor time on a specific processor.</span></span> <span data-ttu-id="5ef3b-112">모든 프로세서의 평균을 확인하려면 **System: %Total Processor Time** 카운터를 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-112">To determine the average for all processors, use the **System: %Total Processor Time** counter instead.</span></span>  
  
 <span data-ttu-id="5ef3b-113">다음과 같은 카운터를 모니터링하여 프로세스 사용을 모니터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-113">Optionally, you can also monitor the following counters to monitor processor usage:</span></span>  
  
-   <span data-ttu-id="5ef3b-114">**Processor: % Privileged Time**</span><span class="sxs-lookup"><span data-stu-id="5ef3b-114">**Processor: % Privileged Time**</span></span>  
  
     <span data-ttu-id="5ef3b-115">프로세서가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O 요청 처리와 같은 Microsoft Windows 커널 명령을 실행하는 데 소비하는 시간의 백분율에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-115">Corresponds to the percentage of time the processor spends on execution of Microsoft Windows kernel commands, such as processing of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O requests.</span></span> <span data-ttu-id="5ef3b-116">**Physical Disk** 카운터가 높을 때 이 카운터가 같이 높으면 더 빠르고 효율적인 디스크 하위 시스템을 설치하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-116">If this counter is consistently high when the **Physical Disk** counters are high, consider installing a faster or more efficient disk subsystem.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5ef3b-117">디스크 컨트롤러와 드라이버가 다르면 커널 처리 시간도 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-117">Different disk controllers and drivers use different amounts of kernel processing time.</span></span> <span data-ttu-id="5ef3b-118">효율적인 컨트롤러와 드라이버를 사용하면 권한 시간이 짧아져 사용자가 애플리케이션을 사용할 수 있는 처리 시간을 확보할 수 있기 때문에 전체 처리량을 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-118">Efficient controllers and drivers use less privileged time, leaving more processing time available for user applications, increasing overall throughput.</span></span>  
  
-   <span data-ttu-id="5ef3b-119">**Processor: %User Time**</span><span class="sxs-lookup"><span data-stu-id="5ef3b-119">**Processor: %User Time**</span></span>  
  
     <span data-ttu-id="5ef3b-120">프로세서가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 같은 사용자 프로세스를 실행하는 데 소비하는 시간의 백분율에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-120">Corresponds to the percentage of time that the processor spends on executing user processes such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5ef3b-121">**시스템: Processor Queue Length**</span><span class="sxs-lookup"><span data-stu-id="5ef3b-121">**System: Processor Queue Length**</span></span>  
  
     <span data-ttu-id="5ef3b-122">프로세서 시간을 기다리는 스레드 수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-122">Corresponds to the number of threads waiting for processor time.</span></span> <span data-ttu-id="5ef3b-123">프로세스의 스레드에 필요한 프로세서 사이클 수가 사용할 수 있는 개수보다 많으면 프로세서 병목 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-123">A processor bottleneck develops when threads of a process require more processor cycles than are available.</span></span> <span data-ttu-id="5ef3b-124">여러 프로세스에서 프로세서 시간을 이용하려고 하면 더 빠른 프로세서를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-124">If more than a few processes attempt to utilize the processor's time, you might need to install a faster processor.</span></span> <span data-ttu-id="5ef3b-125">또는 다중 프로세서 시스템에서는 프로세서를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-125">Or, if you have a multiprocessor system, you could add a processor.</span></span>  
  
 <span data-ttu-id="5ef3b-126">프로세서 사용량을 조사할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 수행하는 작업 유형을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-126">When you examine processor usage, consider the type of work that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs.</span></span> <span data-ttu-id="5ef3b-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 집계 관련 쿼리나 디스크 I/O가 필요 없는 메모리 집중형 쿼리와 같은 계산을 많이 수행한다면 프로세서 시간 전체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs many calculations, such as queries involving aggregates or memory-bound queries that require no disk I/O, 100 percent of the processor's time can be used.</span></span> <span data-ttu-id="5ef3b-128">그 결과 다른 애플리케이션의 성능이 저하되면 작업을 변경해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-128">If this causes the performance of other applications to suffer, try changing the workload.</span></span> <span data-ttu-id="5ef3b-129">예를 들어 컴퓨터가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 실행을 전담하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-129">For example, dedicate the computer to running the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5ef3b-130">많은 클라이언트 요청이 처리되는 경우 사용률이 100%에 가까우면 프로세스가 큐에 대기하고 프로세서 시간을 기다리고 있으며 병목 상태가 발생할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-130">Usage rates around 100 percent, where many client requests are being processed, may indicate that processes are queuing up, waiting for processor time, and causing a bottleneck.</span></span> <span data-ttu-id="5ef3b-131">빠른 프로세서를 추가하여 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef3b-131">Resolve the problem by adding faster processors.</span></span>  
  
  
