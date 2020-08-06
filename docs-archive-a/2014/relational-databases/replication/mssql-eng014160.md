---
title: MSSQL_ENG014160 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3351567a31a0a0384ab8957073ab0457ef0ea7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646352"
---
# <a name="mssql_eng014160"></a><span data-ttu-id="04acf-102">MSSQL_ENG014160</span><span class="sxs-lookup"><span data-stu-id="04acf-102">MSSQL_ENG014160</span></span>
    
## <a name="message-details"></a><span data-ttu-id="04acf-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="04acf-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04acf-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="04acf-104">Product Name</span></span>|<span data-ttu-id="04acf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="04acf-105">SQL Server</span></span>|  
|<span data-ttu-id="04acf-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="04acf-106">Event ID</span></span>|<span data-ttu-id="04acf-107">14160</span><span class="sxs-lookup"><span data-stu-id="04acf-107">14160</span></span>|  
|<span data-ttu-id="04acf-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="04acf-108">Event Source</span></span>|<span data-ttu-id="04acf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="04acf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="04acf-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="04acf-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="04acf-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="04acf-111">Symbolic Name</span></span>||  
|<span data-ttu-id="04acf-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="04acf-112">Message Text</span></span>|<span data-ttu-id="04acf-113">게시 [%s]에 대한 임계값 [%s:%s]이(가) 설정되어 있습니다. 병합 에이전트가 실행 중이고 필요한 요구 사항에 맞는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="04acf-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="04acf-114">이 게시에 대해 하나 이상의 구독이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-114">One or more subscriptions to this publication have expired.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="04acf-115">설명</span><span class="sxs-lookup"><span data-stu-id="04acf-115">Explanation</span></span>  
 <span data-ttu-id="04acf-116">복제를 통해 임박한 구독 만료 등의 여러 조건에 대한</span><span class="sxs-lookup"><span data-stu-id="04acf-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="04acf-117">경고를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-117">This includes imminent subscription expiration.</span></span> <span data-ttu-id="04acf-118">지정된 *보존 기간*내에 동기화되지 않는 구독을 만료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-118">Subscriptions can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="04acf-119">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04acf-119">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="04acf-120">복제 모니터 또는 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)를 사용하여 경고를 설정할 경우 경고가 트리거되는 시기를 결정하는 임계값을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="04acf-120">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="04acf-121">임계값에 도달하거나 임계값이 초과되면 복제 모니터에 경고가 표시되며 Windows 이벤트 로그에 이벤트가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-121">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="04acf-122">또한 임계값에 도달하면 SQL Server 에이전트 경고가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-122">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="04acf-123">자세한 내용은 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md) 및 [프로그래밍 방식으로 복제 모니터링](monitoring-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04acf-123">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04acf-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="04acf-124">User Action</span></span>  
 <span data-ttu-id="04acf-125">이 문제의 해결 방법은 경고 발생 원인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-125">The resolution for this issue depends on the reason the warning was raised:</span></span>  
  
-   <span data-ttu-id="04acf-126">임계값을 초과했지만 구독이 아직 만료되지 않은 경우 구독을 동기화하십시오.</span><span class="sxs-lookup"><span data-stu-id="04acf-126">If the threshold has been exceeded, but the subscription has not yet expired, synchronize the subscription.</span></span> <span data-ttu-id="04acf-127">자세한 내용은 [데이터 동기화](synchronize-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04acf-127">For more information, see [Synchronize Data](synchronize-data.md).</span></span>  
  
-   <span data-ttu-id="04acf-128">에이전트가 실행 중이지만 변경 내용을 제대로 복제하지 않으면 구독이 만료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-128">If the agent has been running, but has not been replicating changes properly, this can cause the subscription to expire.</span></span> <span data-ttu-id="04acf-129">트랜잭션 복제의 경우 배포 에이전트와 로그 판독기 에이전트가 실행 중인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="04acf-129">For transactional replication, make sure that the Distribution Agent and Log Reader Agent are running.</span></span> <span data-ttu-id="04acf-130">병합 복제의 경우 병합 에이전트가 실행 중인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="04acf-130">For merge replication, make sure the Merge Agent is running.</span></span> <span data-ttu-id="04acf-131">이러한 에이전트를 시작하는 방법에 대한 자세한 내용은 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 및 [복제 에이전트 실행 파일 개념](concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04acf-131">For information about how to start these agents, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="04acf-132">구독이 만료된 경우 해당 구독은 구독 유형 및 만료된 기간에 따라 다시 초기화되거나 삭제 후 다시 생성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04acf-132">If the subscription has expired, it must either be reinitialized or dropped and re-created, depending on the type of subscription and how long it has been expired.</span></span> <span data-ttu-id="04acf-133">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04acf-133">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04acf-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04acf-134">See Also</span></span>  
 [<span data-ttu-id="04acf-135">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="04acf-135">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
