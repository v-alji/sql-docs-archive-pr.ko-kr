---
title: SQL Server 확장 이벤트 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 010b7cc29543f266b77aaf180c50173ef9f70346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646607"
---
# <a name="sql-server-extended-events-targets"></a><span data-ttu-id="f4e83-102">SQL Server Extended Events Targets</span><span class="sxs-lookup"><span data-stu-id="f4e83-102">SQL Server Extended Events Targets</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f4e83-103">확장 이벤트 대상은 이벤트 소비자입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-103">Extended Events targets are event consumers.</span></span> <span data-ttu-id="f4e83-104">대상은 파일에 기록하거나 이벤트 데이터를 메모리 버퍼에 저장하거나 이벤트 데이터를 집계할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-104">Targets can write to a file, store event data in a memory buffer, or aggregate event data.</span></span> <span data-ttu-id="f4e83-105">대상은 동기적 또는 비동기적으로 데이터를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-105">Targets can process data synchronously or asynchronously.</span></span>  
  
 <span data-ttu-id="f4e83-106">확장 이벤트는 대상이 세션당 단 한 번만 이벤트를 수신하도록 설계되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-106">The Extended Events design ensures that targets are guaranteed to receive events once and only once per session.</span></span>  
  
 <span data-ttu-id="f4e83-107">확장 이벤트 세션에 사용할 수 있도록 확장 이벤트에서 제공하는 대상은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-107">Extended Events provide the following targets that you can use for an Extended Events session:</span></span>  
  
-   [<span data-ttu-id="f4e83-108">이벤트 카운터</span><span class="sxs-lookup"><span data-stu-id="f4e83-108">Event counter</span></span>](../../2014/database-engine/event-counter-target.md)  
  
     <span data-ttu-id="f4e83-109">확장 이벤트 세션 동안 발생하는 모든 지정된 이벤트의 수를 셉니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-109">Counts all specified events that occur during an Extended Events session.</span></span> <span data-ttu-id="f4e83-110">전체 이벤트 컬렉션의 오버헤드를 증가시키지 않으면서 작업 특성에 대한 정보를 얻는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-110">Use to obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="f4e83-111">이 대상은 동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-111">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="f4e83-112">이벤트 파일</span><span class="sxs-lookup"><span data-stu-id="f4e83-112">Event file</span></span>](../../2014/database-engine/event-file-target.md)  
  
     <span data-ttu-id="f4e83-113">완료된 메모리 버퍼에서 디스크로 이벤트 세션 출력을 쓰는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-113">Use to write event session output from complete memory buffers to disk.</span></span> <span data-ttu-id="f4e83-114">이 대상은 비동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-114">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="f4e83-115">이벤트 쌍</span><span class="sxs-lookup"><span data-stu-id="f4e83-115">Event pairing</span></span>](../../2014/database-engine/event-pairing-target.md)  
  
     <span data-ttu-id="f4e83-116">잠금 획득 및 잠금 해제와 같이 많은 종류의 이벤트는 쌍으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-116">Many kinds of events occur in pairs, such as lock acquires and lock releases.</span></span> <span data-ttu-id="f4e83-117">쌍을 이루는 집합에서 지정된 쌍 이벤트가 발생하지 않는 경우를 확인하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-117">Use to determine when a specified paired event does not occur in a matched set.</span></span> <span data-ttu-id="f4e83-118">이 대상은 비동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-118">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="f4e83-119">ETW(Windows용 이벤트 추적)</span><span class="sxs-lookup"><span data-stu-id="f4e83-119">Event Tracing for Windows (ETW)</span></span>](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     <span data-ttu-id="f4e83-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이벤트와 Windows 운영 체제 또는 애플리케이션 이벤트 데이터의 상관 관계를 파악하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-120">Use to correlate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events with Windows operating system or application event data.</span></span> <span data-ttu-id="f4e83-121">이 대상은 동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-121">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="f4e83-122">히스토그램</span><span class="sxs-lookup"><span data-stu-id="f4e83-122">Histogram</span></span>](../../2014/database-engine/histogram-target.md)  
  
     <span data-ttu-id="f4e83-123">지정된 이벤트 열 또는 동작을 기반으로 지정된 이벤트가 발생한 횟수를 계산하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-123">Use to count the number of times that a specified event occurs, based on a specified event column or action.</span></span> <span data-ttu-id="f4e83-124">이 대상은 비동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-124">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="f4e83-125">링 버퍼</span><span class="sxs-lookup"><span data-stu-id="f4e83-125">Ring buffer</span></span>](../../2014/database-engine/ring-buffer-target.md)  
  
     <span data-ttu-id="f4e83-126">FIFO(선입선출) 또는 이벤트별 FIFO 방식으로 메모리에 이벤트 데이터를 저장하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-126">Use to hold the event data in memory on a first-in first-out (FIFO) basis, or on a per-event FIFO basis.</span></span> <span data-ttu-id="f4e83-127">이 대상은 비동기 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f4e83-127">This is an asynchronous target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e83-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4e83-128">See Also</span></span>  
 <span data-ttu-id="f4e83-129">[확장 이벤트](../relational-databases/extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="f4e83-129">[Extended Events](../relational-databases/extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="f4e83-130">[확장 이벤트 패키지 SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="f4e83-130">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="f4e83-131">[확장 이벤트 세션 SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="f4e83-131">[SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span></span>  
 [<span data-ttu-id="f4e83-132">SQL Server 확장 이벤트 엔진</span><span class="sxs-lookup"><span data-stu-id="f4e83-132">SQL Server Extended Events Engine</span></span>](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
