---
title: 잠금 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a202279021e3e6c7c3c44a167792bb9439567aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647692"
---
# <a name="locks-event-category"></a><span data-ttu-id="66b89-102">잠금 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="66b89-102">Locks Event Category</span></span>
  <span data-ttu-id="66b89-103">**Locks** 이벤트 범주의 이벤트 클래스를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에서 잠금 작업을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-103">Use the event classes in the **Locks** event category to monitor locking activity in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="66b89-104">이러한 이벤트 클래스를 사용하면 여러 사용자들이 동시에 데이터를 읽고 수정하여 발생되는 잠금 문제를 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-104">These event classes can help you investigate locking problems caused by multiple users reading and modifying data concurrently.</span></span>  
  
 <span data-ttu-id="66b89-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 종종 많은 수의 잠금을 처리하기 때문에 추적하는 동안 **Locks** 이벤트 클래스를 캡처하면 오버헤드가 증가하고 추적 파일이나 테이블도 많아집니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-105">Because the [!INCLUDE[ssDE](../../includes/ssde-md.md)] often processes many locks, capturing the **Locks** event classes during a trace can incur significant overhead and result in large trace files or tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66b89-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="66b89-106">In This Section</span></span>  
  
|<span data-ttu-id="66b89-107">항목</span><span class="sxs-lookup"><span data-stu-id="66b89-107">Topic</span></span>|<span data-ttu-id="66b89-108">Description</span><span class="sxs-lookup"><span data-stu-id="66b89-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="66b89-109">Deadlock Graph 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-109">Deadlock Graph Event Class</span></span>](deadlock-graph-event-class.md)|<span data-ttu-id="66b89-110">교착 상태에 대한 XML 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-110">Provides an XML description of a deadlock.</span></span>|  
|[<span data-ttu-id="66b89-111">Lock:Acquired 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-111">Lock:Acquired Event Class</span></span>](lock-acquired-event-class.md)|<span data-ttu-id="66b89-112">테이블의 행과 같은 리소스에 대해 잠금을 획득했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-112">Indicates that a lock has been acquired on a resource, such as a row in a table.</span></span>|  
|[<span data-ttu-id="66b89-113">Lock:Cancel 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-113">Lock:Cancel Event Class</span></span>](lock-cancel-event-class.md)|<span data-ttu-id="66b89-114">교착 상태 등을 방지하기 위해 잠금을 획득하기 전에 취소된 잠금 요청을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-114">Tracks requests for locks that were canceled before the lock was acquired (for example, to prevent a deadlock).</span></span>|  
|[<span data-ttu-id="66b89-115">Lock:Deadlock Chain 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-115">Lock:Deadlock Chain Event Class</span></span>](lock-deadlock-chain-event-class.md)|<span data-ttu-id="66b89-116">교착 상태 조건이 발생한 시기 및 관련 개체를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-116">Monitors when deadlock conditions occur and which objects are involved.</span></span>|  
|[<span data-ttu-id="66b89-117">Lock:Deadlock 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-117">Lock:Deadlock Event Class</span></span>](lock-deadlock-event-class.md)|<span data-ttu-id="66b89-118">다른 트랜잭션에 의해 이미 잠겨 있는 리소스에 대해 트랜잭션이 잠금을 요청하여 교착 상태가 발생한 시기를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-118">Tracks when a transaction has requested a lock on a resource already locked by another transaction, resulting in a deadlock.</span></span>|  
|[<span data-ttu-id="66b89-119">Lock:Escalation 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-119">Lock:Escalation Event Class</span></span>](lock-escalation-event-class.md)|<span data-ttu-id="66b89-120">미세 잠금이 성긴 잠금으로 변환되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-120">Indicates that a finer-grained lock has been converted to a coarser-grained lock.</span></span>|  
|[<span data-ttu-id="66b89-121">Lock:Released 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-121">Lock:Released Event Class</span></span>](lock-released-event-class.md)|<span data-ttu-id="66b89-122">잠금이 해제된 시기를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-122">Tracks when a lock is released.</span></span>|  
|[<span data-ttu-id="66b89-123">Lock:Timeout&#40;timeout &#62; 0&#41; 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-123">Lock:Timeout &#40;timeout &#62; 0&#41; Event Class</span></span>](lock-timeout-timeout-0-event-class.md)|<span data-ttu-id="66b89-124">요청된 리소스에 대한 다른 트랜잭션의 차단 잠금 때문에 잠금 요청을 완료할 수 없는 시기를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-124">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span> <span data-ttu-id="66b89-125">이 이벤트는 잠금 제한 시간 값이 0보다 큰 경우에만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-125">This event occurs only in situations where the lock time-out value is greater than zero.</span></span>|  
|[<span data-ttu-id="66b89-126">Lock:Timeout 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="66b89-126">Lock:Timeout Event Class</span></span>](lock-timeout-event-class.md)|<span data-ttu-id="66b89-127">요청된 리소스에 대한 다른 트랜잭션의 차단 잠금 때문에 잠금 요청을 완료할 수 없는 시기를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="66b89-127">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span>|  
  
  
