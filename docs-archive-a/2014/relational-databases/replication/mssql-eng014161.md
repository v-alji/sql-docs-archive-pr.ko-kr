---
title: MSSQL_ENG014161 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8cf85181e444385e1a3908761ba71414b68cf3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638675"
---
# <a name="mssql_eng014161"></a><span data-ttu-id="29999-102">MSSQL_ENG014161</span><span class="sxs-lookup"><span data-stu-id="29999-102">MSSQL_ENG014161</span></span>
    
## <a name="message-details"></a><span data-ttu-id="29999-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="29999-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29999-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="29999-104">Product Name</span></span>|<span data-ttu-id="29999-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29999-105">SQL Server</span></span>|  
|<span data-ttu-id="29999-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="29999-106">Event ID</span></span>|<span data-ttu-id="29999-107">14161</span><span class="sxs-lookup"><span data-stu-id="29999-107">14161</span></span>|  
|<span data-ttu-id="29999-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="29999-108">Event Source</span></span>|<span data-ttu-id="29999-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29999-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29999-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="29999-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="29999-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="29999-111">Symbolic Name</span></span>||  
|<span data-ttu-id="29999-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="29999-112">Message Text</span></span>|<span data-ttu-id="29999-113">게시 [%s]에 대한 임계값 [%s:%s]이(가) 설정되어 있습니다. 병합 에이전트가 실행 중이고 필요한 요구 사항에 맞는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="29999-114">로그 판독기와 배포 에이전트가 실행 중이고 대기 시간 요구 사항에 맞는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-114">Make sure that the logreader and distribution agents are running and can match the latency requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29999-115">설명</span><span class="sxs-lookup"><span data-stu-id="29999-115">Explanation</span></span>  
 <span data-ttu-id="29999-116">복제를 통해 임박한 구독 만료 등의 여러 조건에 대한</span><span class="sxs-lookup"><span data-stu-id="29999-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="29999-117">여기에는 트랜잭션 구독에 대해 지정한 대기 시간 초과가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="29999-117">This includes exceeding a specified latency for transactional subscriptions.</span></span> <span data-ttu-id="29999-118">대기 시간은 게시자에서 데이터 변경 내용이 커밋되는 시점과 구독자에서 해당 변경 내용이 커밋되는 시점 간의 시간 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="29999-118">Latency is the period of time that elapses between a data change being committed at the Publisher and the corresponding change being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="29999-119">복제 모니터 또는 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)를 사용하여 경고를 설정할 경우 경고가 트리거되는 시기를 결정하는 임계값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="29999-120">임계값에 도달하거나 임계값이 초과되면 복제 모니터에 경고가 표시되며 Windows 이벤트 로그에 이벤트가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="29999-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="29999-121">또한 임계값에 도달하면 SQL Server 에이전트 경고가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="29999-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="29999-122">자세한 내용은 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md) 및 [프로그래밍 방식으로 복제 모니터링](monitoring-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29999-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29999-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="29999-123">User Action</span></span>  
 <span data-ttu-id="29999-124">구독이 대기 시간 임계값을 초과할 경우 시스템에 성능 문제가 있는지 확인하거나 임계값 조정 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29999-124">If a subscription exceeds a latency threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="29999-125">복제를 구성한 후에는 애플리케이션 및 토폴로지에 일반적으로 사용되는 작업과의 복제 동작 방식을 결정할 수 있는 성능 기준선을 개발하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="29999-126">이때 임계값에 대해 적절한 값을 설정할 수 있도록 이 기준선의 대기 시간을 포함하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-126">Include latency in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="29999-127">임계값이 적절하지만 초과된 경우 시스템의 성능 병목 위치를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29999-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="29999-128">복제 성능 모니터링 및 문제 해결 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="29999-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   [<span data-ttu-id="29999-129">트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="29999-129">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [<span data-ttu-id="29999-130">복제 모니터로 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="29999-130">Monitor Performance with Replication Monitor</span></span>](monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a><span data-ttu-id="29999-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29999-131">See Also</span></span>  
 [<span data-ttu-id="29999-132">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="29999-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
